# Workspace Tutorial

In this tutorial we are going to create and work for the first time with an NDP workspace. 

## Setup

1. Go to the National Data Platform [site](https://nationaldataplatform.org/) and login.
2. On the top bar menu, select *Workspaces*. At this point, you will have no workspaces. 
3. Select *Create a workspace* and fill the form fields. For the purposes of this tutorial, you can fill it with the following info:
    - **Name**: demo-workspace
    - **Description**: This is my first NDP Workspace
    - **Instructional Text**: Use this workspace as a demo
4. Once you fill the form, click on *Open new workspace*. 

## Adding Resources

When a new workspace is launched, it automatically becomes the **current workspace**. All resources added from the catalog will be associated with this active workspace. If you have multiple workspaces, you can switch the **current workspace** by selecting the *Switch* button in the workspace box of the desired workspace. This will designate it as the **current workspace** moving forward.

### Adding GitHub URL

The first resource we'll add to the workspace is a GitHub repository.

1. Click on the **CURRENT WORKSPACE** box.
2. Select Add a GitHub URL. For this tutorial, use the following URL: `https://github.com/pramonettivega/workspace-tutorial.git`. You can view the sample repository at this [link](https://github.com/pramonettivega/workspace-tutorial).
3. Enter the GitHub URL in the provided field and click *Add*.

!!! info "Provide the .git link"
    ⚠️ **Important:** Make sure the GitHub link you provide ends with `.git`.  
    Example: `https://github.com/username/repo.git`

### Adding data

Now we will add data from the data catalog into our workspace.

1. Go to the Data Catalog
2. Locate the dataset to add to the workspace. In this tutorial, we are going to use *Unifor Fuels Quic-Fire Simulation Runs Ensemble*. To find it, search for the term *PGML*
3. Once you locate the dataset, click on *Add to workspace*. This will add the data to the **CURRENT WORKSPACE**. That's why it is important to select the correct workspace when adding resources.

At this point, we have added data and a source code to our workspace. Now we can proceed to load our workspace into JupyterHub. 

## Using your workspace in JupyterHub

1. Go to [NDP JupyterHub](https://ndp-jupyterhub.nrp-nautilus.io/hub/spawn)
2. For the purposes of this demo, we don't need major resources. Select the following fields:
    - **Region**: Any 
    - **GPU's**: 0
    - **Cores**: 1
    - **RAM, GB**: 16
    - **GPU Type**: Any
    - **Select Pre-Built Image**: Minimal NDP Starter Jupyter Lab
    - **Architecture**: amd64
3. Click on *Start* and wait for your server to start running. 
4. Once you're inside JupyterLab, at your left you will locate the NDP Extension. Click on the *NDP* button. 
5. In the extension, select your workspace using the dropdown menu. 
6. Go to the third section of the extension, and click on *Clone into current folder*. This will clone the repo we added into our **current folder**. 

!!! info "Verify your current folder"
    ⚠️ **Important:** In the NDP extension, all selected files will be downloaded to the current folder. If the current folder is not your `User_Persistent_Storage`, your files will be lost when the session ends. To preserve your files, navigate to the persistent storage folder in the file explorer before returning to the NDP extension via the NDP button in the left menu.

7. Ensure that the folder selected in the **current folder** box is your GitHub repository folder. If it contains a `requirements.txt` file, you can install the required packages by clicking *Install requirements.txt*. Navigate to the `workspace-tutorial` folder, return to the extension, and then click the button to install the packages.

8. In the datasets dropdown menu, you will see all the datasets that you previously added to the workspace, along with its associated resources. For this demo, you will select the last file on the list (`uniform-pgml-success_list_simulation_run.csv`) and click on *Add resources to current folder*. Make sure to be in the correct **current folder** (in this case, the GitHub repository folder).

9. With your libraries installed and the data downloaded, go to the Jupyter Notebook included in the repository folder (`NDP_PGML_EDA.ipynb`) and follow the instructions for its execution.

!!! info "Environments are not persistent"
    ⚠️ **Important:** In the current version of NDP, installed libraries and packages are not saved. Each time you return, you will need to reinstall the packages from your `requirements.txt` file before you can start working.


In this tutorial we have created our first workspace, added resources to it and executed a Jupyter Notebook. Use NDP workspaces for the development of your projects.