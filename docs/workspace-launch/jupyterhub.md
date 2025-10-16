# NDP JupyterHub

[NDP JupyterHub](https://ndp-jupyterhub.nrp-nautilus.io/hub/spawn) service (hosted by NRP's [Nautilus](https://dash.nrp-nautilus.io/)) allows users to develop their workflows in a user-friendly environment.

## NDP Widget
The NDP Widget is a JupyterLab extension that provides an interactive interface to access key features of the NDP platform. This widget is accessible from the left menu within the JupyterHub service.

The NDP Widget consists of the following components:

- **File Manager** 
- **GIT Extension**
- **Current Folder:** Displays the current folder you are working in, indicating the directory where files will be downloaded or git directories cloned.

- **Select your workspace:** Displays a list of your workspaces and educational modules. Selecting a workspace updates the resources displayed in the following sections.

- **Clone GitHub repository into workspace:** Displays the GitHub repositories associated with the selected workspace. You can choose a specific repository and clone it to your *Current Folder*. 

- **Install requirements.txt:** Installs a `requirements.txt` file in the current kernel if it exists in the *Current Folder*. A `pip_install.log` file is generated, confirming the successful installation of libraries or indicating any installation failures. Take into consideration that currently environments are not persistent. For guidance of making persistent environments, review the [*Use your own JupyterHub image*](../workspace-launch/jupyterhub.md) page.

- **Add datasets and resources from workspace:** Displays data and resources associated with the selected workspace. You can choose specific resources and download them to your *Current Folder*. Additionally, you can organize your downloads by selecting the checkbox to automatically create a directory with the name of the dataset, which will contain the downloaded files within your *Current Folder*.

## User_Persistent_Storage

Once JupyterHub is launched, you will notice a `_User-Persistent-Storage_` directory. This directory corresponds to your persistent storage. Make sure to save your work in this directory, otherwise it will be lost when you disconnect from your server.

Every user is given a **10GB storage**. If you need more space, contact `ndp@sdsc.edu`. 

## Set Up

Once in the Hub, you can set up your server by selecting the following fields:
    
    * Region
    * GPUs
    * Cores
    * RAM, GB
    * GPU Type 
    * /dev/shm for pytorch
    * Image
    * Architecture

Prior to initiate your server, you can consult the [availabe resources page](https://portal.nrp-nautilus.io/resources) 

## R Studio

R Studio can be deployed through the JupyterHub service by selecting the pre-built image. When setting up your server, select `Minimal NDP Starter Jupyter Lab + R Studio`. 

<img src="../images/r-studio-image.png" style="border: 2px solid black;">

Once your server is running, select RStudio from the launcher window. This will open a new tab with the RStudio interface, ready for you to begin your work.

Please note: the NDP Widget is not available within the RStudio environment. To continue using the Widger features, keep your JupyterLab session open in a separate tab or window.

As with all Jupyter-launched servers, packages installed within RStudio are not persistent. Any packages you add during a session will be lost once the server is stopped. To ensure reproducibility and persistence:

- Maintain a list of required packages within your project (e.g., requirements.R or a project-specific script).

- For long-term use, consider creating a customized Docker image that includes all necessary R packages pre-installed.


## Stoping your server

Once you have finished your work, make sure to **stop your server:**

1. On the top left, click on *File*, followed by *Hub Control Panel*.
2. If you're only running one server, click on *Stop My Server*. If you're running multiple servers, make sure to stop the right server.
