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

When a new workspace is launched, it automatically becomes the **current workspace**. 

<img src="../images/current-workspace.png">

All resources added from the catalog will be associated with this active workspace. If you have multiple workspaces, you can switch the **current workspace** by selecting the *Switch* button in the workspace box of the desired workspace. 

<div style="text-align: center;">
    <img src="../images/switch.png" alt="Switch" width="300">
</div>

This will designate it as the **current workspace** moving forward.

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

1.Go to [NDP JupyterHub](https://ndp-jupyterhub.nrp-nautilus.io/hub/spawn)

2.For the purposes of this demo, we don't need major resources. Select the following fields:

    - Region: Any 
    - GPU's: 0
    - Cores: 1
    - RAM, GB: 16
    - GPU Type: Any
    - Select Pre-Built Image: Minimal NDP Starter Jupyter Lab
    - Architecture: amd64

3.Click on *Start* and wait for your server to start running. 

4.Once you're inside JupyterLab, at your left you will locate the NDP Extension. Click on the *NDP* button. 

<img src="../images/ndp-button.png">

5.In the extension, select your workspace using the dropdown menu. 

<div style="text-align: center;">
    <img src="../images/select-workspace.png" alt="Select workspace" width="300">
</div>

6.At the top of the extension, locate the *current folder*. By default, you will start in the `root/` folder, but keep in mind that files placed here **will not persist across sessions**. To ensure your work is saved for future sessions, switch to the `User_Persistent_Storage` folder. To do this, click on the *current folder* box, navigate to the desired folder (`User_Persistent_Storage`), and then click the NDP button to return to the extension.
 
<div style="text-align: center;">
    <img src="../images/persistent-storage.png" alt="User Persistent Storage" width="300">
</div>

7.Go to the third section of the extension, and click on *Clone into current folder*. This will clone the repo we added into our *current folder* (which is the `User_Persistent_Storage` if you made the change in the previous step, or the root if you did not). 

8.Navigate to the `workspace-tutorial` folder and return to the extension. The folder contains a `requirements.txt` file, which you can install by clicking *Install requirements.txt*. 

<div style="text-align: center;">
    <img src="../images/requirements.png" alt="requirements.txt" width="300">
</div>

Click the button to install the packages.

!!! info "Environments are not persistent"
    ⚠️ **Important:** In the current version of NDP, installed libraries and packages are not saved. Each time you return, you will need to reinstall the packages from your `requirements.txt` file before you can start working.

9.Make sure to be in the correct *current folder* (in this case, the GitHub repository folder). In the datasets dropdown menu, you will see all the datasets that you previously added to the workspace, along with its associated resources. For this demo, you will select the last file on the list (`uniform-pgml-success_list_simulation_run.csv`) and click on *Add resources to current folder*. 

10.With your libraries installed and the data downloaded, go to the Jupyter Notebook included in the repository folder (`NDP_PGML_EDA.ipynb`) and follow the instructions for its execution.

<div style="text-align: center;">
    <img src="../images/files-list.png" alt="Files" width="300">
</div>

In this tutorial we have created our first workspace, added resources to it and executed a Jupyter Notebook. Use NDP workspaces for the development of your projects.