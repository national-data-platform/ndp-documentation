# Launching your own JupyterHub in AWS

Users with AWS credit can deploy 

The following guidelines assume that the user implementing the customized cluster has:

- Acquired its own AWS credits
- Possess a good understanding of the AWS Platform.
- Possess basic knowledge of Kubernetes. 

## Cluster Admin Role

- Create IAM user
- Assign policies
- Under security credentials, click Create access key. Select CLI as use case. Add an useful tag.
- Install CLI in your local system
- Confirm installation via `aws --version`
- Add your access key and secret via `aws configure`


## Setting Up the Elastic Kubernetes Cluster

Since JupyterHub is deployed on Kubernetes, we will use **Amazon Elastic Kubernetes Service (EKS)** to manage and orchestrate the deployment. This guide outlines a general functional implementation using Auto Mode for pod deployment. For more advanced configurations or custom networking setups, refer to the official [AWS EKS documentation](https://docs.aws.amazon.com/eks/).

### Creating your cluster

- In the AWS Management Console, search for **EKS** and open the service.

- Click *Create cluster*.

- In the configuration page:

    - **Cluster mode**: Keep Auto Mode.

    - **Cluster name**: Assign a descriptive name to your cluster (e.g., ndp-jupyterhub-cluster).

    - **Kubernetes version**: Choose a recent supported version (this example uses 1.33).

- Under **Create a recommended role**:

    - Click *Create role*.

    - In the EKS Auto cluster section, keep the default settings and click *Next*.

- In **Add permissions**, keep the defaults and click *Next*.

- In **Name, review, and create**, keep the defaults and click *Create role*.

- In a separate tab, go to the **IAM console**:

    - Create a new user (for example, `cluster-admin`).

    - Assign the EKS role you just created to this user. This user will later be used to authenticate and manage your cluster from your local terminal.

- Return to the EKS console. Keep the remaining configuration options as default and click Create.

Note: The cluster provisioning process can take several minutes to complete.

### Connecting to the EKS Cluster from Your Local Terminal

This section assumes that both the **AWS CLI** and **kubectl (Kubernetes CLI)** are already installed and configured on your computer. If not, follow the [AWS CLI installation guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) and the [Kubernetes CLI](https://kubernetes.io/docs/tasks/tools/) setup guide before proceeding.

- In your clusters page, click on *Access*.
- Click on create to associate a user to the access policies. 
- Select the IAM user you created earlier and assign the following two policies:
    - AmazonEKSAdminPolicy
    - AmazonEKSClusterAdminPolicy
- Click on Create 
- In your local terminal reate or update a kubeconfig via the command `aws eks update-kubeconfig --region region-code --name my cluster` 
- Confirm the context was added to your config file via `kubectl config get-contexts`
- Confirm that 2 base pods are running via `kubectl get pods -n kube-system`. Two metrics server pods should be running. Optially, you can remove one of them to reduce costs, as these are replicas. You can do this via `kubectl scale deployment metrics-server --replicas=1 -n kube-system` 

## Deploying JupyterHub

To deploy JupyterHub on your EKS cluster, you will use a preconfigured deployment template available on GitHub. This template includes the core Helm chart configuration, authentication setup, and storage integration.

### Adding JupyterHub Secret and Client

- Create a dedicated namespace for JupyterHub: `kubectl create namespace jhub`. It is recommended to keep this namespace name (`jhub`), as many configuration fields and manifests are preconfigured to reference it.
- Request your Keycloak client ID and client secret from the NDP team. These credentials enable authentication through the centralized identity system.
- Clone the JupyterHub deployment template repository: `git clone wstc/jupyterhub.git`
- Open the cloned repository and edit the file `jupyterhub_secret.yaml` within the `helm/ndp-hub` directory.
- Add the client ID and client secret you received from the NDP team.
- Add the secret to your Kubernetes namespace: `kubectl create secret generic jupyterhub-secret  --from-file=value.yaml=jupyterhub_secret.yaml -n jhub`


### Configuring the Storage Class

- In the AWS console, navigate to your EKS cluster.
- Go to the *Add-ons* tab. Click on *Get more add-ons* and select **Amazon EBS CSI Driver**.
- Follow the prompts to create the recommended IAM roles.
- Keep the default configuration and click *Create*.
- Verify that the EBS CSI Driver pods are running: `kubectl get pods -n kube-system`
- Apply the EBS StorageClass configuration `kubectl apply -f ebs-storageclass.yaml`. This file uses the same template provided in [AWS documentation](http://docs.aws.amazon.com/eks/latest/userguide/create-storage-class.html).
- In your Helm configuration file (`values.yaml`), set the storageClassName to use EBS:

```
storageClassName: auto-ebs-sc
```

### Installing NGINX

You will use NGINX Ingress Controller to expose JupyterHub to external users. This setup uses Helm for deployment and AWS Load Balancer annotations to configure public access.

- Install Helm locally if it is not already installed. See the Helm installation guide for detailed instructions.
- Add the official ingress-nginx Helm repository: `helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx`
- Create a dedicated namespace for NGINX: `kubectl create namespace ingress-nginx`
- Install the Helm chart in that namespace: `helm install ingress-nginx ingress-nginx/ingress-nginx --namespace ingress-nginx`
- Verify that the NGINX Ingress Controller pod is running: `kubectl get pods -n ingress-nginx`

### Configuring Networking and Load Balancer

- In the AWS Management Console, open the VPC service.
- Navigate to Subnets.
- For each subnet, click Manage tags and create a new tag associated with your cluster:
```
- Key: kubernetes.io/cluster/<your-cluster-name>
- Value: owned
```

- Patch the NGINX service to make it internet-facing:
```
kubectl patch svc ingress-nginx-controller  \
  -n ingress-nginx \
  -p '{"metadata": {"annotations": {"service.beta.kubernetes.io/aws-load-balancer-scheme": "internet-facing"}}}'
```
- List the created load balancers: `aws elbv2 describe-load-balancers --region <your-region>`. The response will have the security groups associated to the subnets. 
- Authorize inbound HTTP traffic to the associated security group:
```
aws ec2 authorize-security-group-ingress \
  --group-id <sg-id> \
  --protocol tcp \
  --port 80 \
  --cidr 0.0.0.0/0
```
- Retrieve the External IP of the LoadBalancer: `kubectl get svc -n ingress-nginx`
- Copy the EXTERNAL-IP value and update the corresponding variables in your `values.yaml`.
- Finally, contact the NDP team to associate the external IP with your Keycloak client for authentication integration.

### Deploying the Hub

- Follow the installation steps described in the template repository’s `README.md`. This will ensure all required Helm dependencies and configurations are properly initialized.
- Inside the repository’s helm directory, locate the Makefile.
- Verify that the namespace value matches your deployment namespace (`jhub`).
- Add or update your `KUBECONTEXT` to point to your EKS cluster.
- Deploy JupyterHub using the Makefile command: `make deploy`.
- Confirm that the JupyterHub components are running: `kubectl get pods -n jhub`. You should see both the hub and proxy pods in a Running state.
- Open a web browser and navigate to the External IP you configured earlier for your NGINX LoadBalancer.
- You should now see the JupyterHub spawner interface exposed.

## Setting the Shared Storage

To enable shared storage for your cluster, we’ll use **Amazon Elastic File System (EFS)**. This guide provides a general functional implementation. For more advanced configurations or customizations, refer to the official [AWS EFS documentation](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html).


### Creating the File System

- In the AWS Management Console, search for **EFS** in the services search bar.

- Select *Create File System*.

- Keep the default settings and click *Create File System* again.

- Once the file system is created, return to the EKS service and select your cluster.

- In your cluster page, select *Add-ons*, then click *Get more add-ons*.

- Locate and select **Amazon EFS CSI Driver**, then click *Next*.

- On the setup page, accept the default options to create a **new IAM role**.

- Review the configuration and click *Create*.

### Adding the File System to the Cluster

- Use the following YAML template to create a new StorageClass for your cluster. Save it as `efs-storage-class.yaml`.

- In the Elastic File System console, copy your FileSystemID and replace the placeholder value in the YAML file.

- Apply the configuration:

```
kubectl apply -f efs-storage-class.yaml
```

- Verify the creation:

```
kubectl get storageclass
```

### Granting JupyterHub Access to the File System

- Open the **IAM console** and create a new role for JupyterHub.

- Attach the following policies:

    - access-point-control-policy

    - AmazonEFSCSIDriverPolicy

- Copy the **ARN** of the newly created role and add it to your Helm chart’s values.yaml under:

```
serviceAccount:
  annotations:
    eks.amazonaws.com/role-arn: <YOUR_ROLE_ARN>
```

- In your JupyterHub configuration (`spawner.py`):

    - Uncomment and update the EFS client section with your **FileSystemID**.

    - Uncomment the `create_access_point` function.

- Return to the EFS console and select your File System.

- Go to the *Network* tab and locate the Security Group associated with your EC2 instances. Copy this Security Group ID. You’ll also need to copy the Security Group ID associated with your EKS cluster.

- In the **EC2 console**:

    1. Open the EC2 instances’ security group.

    2. Choose *Edit inbound rules*, add a new rule:

        - Type: *NFS*

        - Source: your cluster’s Security Group

    3. Save the rule.

    4. Open the cluster’s security group:

    5. Choose *Edit outbound rules*, add a new rule:

        - Type: NFS

        - Destination: the EC2 Security Group

    6. Save the rule.

- Redeploy your JupyterHub to apply the new configurations. Existing user pods will remain unaffected, as only the main Hub service is redeployed. 

Your cluster now includes a shared EFS-based file system. Each user group will automatically receive its own shared directory within the JupyterHub environment.



