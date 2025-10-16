# Resource Allocation

Allocating computational resources efficiently is one of the most challenging aspects of deploying JupyterHub environments. As noted in the [official JupyterHub documentation on capacity planning](https://jupyterhub.readthedocs.io/en/latest/explanation/capacity-planning.html), there is no single correct answer to the common question:

*“I have X number of users who will be working on this — how much compute do I need?”*

## Developing and Testing Workspaces

Before finalizing resource settings, educators are strongly encouraged to develop and test all required workspaces for their educational CollabStudio. This helps determine realistic resource needs and ensures smooth classroom execution.

1. **Register your data.** Ensure all datasets are properly registered and accessible from within the workspace.

2. **Test under multiple setups.** Experiment with different configurations (varying RAM, CPU cores, or GPU availability) to evaluate performance.

3. **Optimize for cost and efficiency.** Choose the minimal configuration that guarantees optimal performance for your workloads, and set this as the default to control expenses.

## Reserving Resources in Your Hub

The current AWS JupyterHub implementation uses EKS Auto Mode, which automatically provisions resources based on pod demands. This configuration does not impose a hard limit on the number of nodes available to the cluster.

If you wish to enforce node limits or control scaling behavior, you can create a customized EKS configuration. However, note that restricting node availability may limit users’ ability to launch new workspaces during periods of high demand.

## Assigning Resources to Users

There are several strategies for managing how resources are allocated to students within JupyterHub:

### Option A: Define resources per workspace form

- Specify the amount of CPU, RAM, or GPU each workspace should reserve directly within its form configuration.

- Encourage educators to use this setup to monitor and manage resource utilization across their namespace.

### Option B: Fix resource values in the JupyterHub spawner

- In your custom spawner configuration, predefine resource limits and requests.

- This approach ensures consistency and prevents students from modifying resource values.

### Option C (Proposed): Dynamic resource passing via CollabStudio form

- Integrate resource definitions directly into the CollabStudio workspace form.

- These values are then transferred to the spawner automatically, ensuring each launched workspace uses the pre-approved configuration.
