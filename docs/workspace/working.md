# Working with a Workspace - Tutorial

In this tutorial, you’ll learn how to work with a Workspace in JupyterHub.

At this point, you should have completed the Set Up Workspace tutorial. If you haven’t done so yet, we highly recommend completing it first.

In the previous tutorial, you set up your first Workspace. Now, you'll launch it and begin working within JupyterHub.

#### 1. Launch Your Workspace in JupyterHub

- Go to your Dashboard and click the *View* button for your Demo Workspace.

- Scroll down and click the *JupyterHub* button.

<img src="../images/jupyter-button.png" style="border: 2px solid black;">

You can find the same button for any Workspace within your research projects or group workspaces.

<img src="../images/jupyter-button.png" style="border: 2px solid black;">

#### 2. Configure Your Resources

Once in JupyterHub, reserve the following resources:

    Region: West
    Zone: UCSD
    GPUs: 0
    Cores: 1
    RAM: 8 GB
    GPU Type: Any
    /dev/shm for pytorch: Do not check
    Image: Minimal NDP Starter JupyterLab
    Architecture: amd64

Click on *Start* and wait for your server to start running. 

#### 3. Troubleshooting Login Issues

If you encounter an error when launching the server:

<img src="../images/error.png" style="border: 2px solid black;">

- Click Logout (top-right corner).

- Log in again and repeat step 2.

#### 4. Navigate and Set Up Your Workspace

- On the left panel, locate the [NDP Widget](../workspace/overview.md#ndp-widget).

- Click the *Current Folder* window.

<img src="../images/current-folder.png" style="border: 2px solid black;">

- Double-click on your User Persistent Storage to work in a folder with permanent storage (10GB limit).

- Return to the NDP Widget by clicking the *NDP* button on the left panel.

<img src="../images/ndp-button.png" style="border: 2px solid black;">


- Open the *Select Workspace* dropdown and choose *Demo Workspace*.

- Click *Clone into current folder* and wait for the repository to finish cloning.

<img src="../images/clone.png" style="border: 2px solid black;">

- Go back to *Current Folder* and open the newly created `demo-workspace` directory.

#### 5. Install Workspace Dependencies

- Return to the NDP Widget, and click *Install requirements.txt.*

- Wait for the log file to appear.

<img src="../images/requirements.png" style="border: 2px solid black;">

!!! info 
    If the .log file doesn't appear, click the button again. Sometimes, the installation completes but the log file isn’t generated on the first attempt.

#### 6.  Add the Dataset

- In the NDP Widget, under *Add Selected Files*, choose:

    - Dataset: `weather-station-measurements`

    - Resource: `San Diego Weather Sample`

- Check *Create Dataset Folder*.

- Click Add resources to current folder to download the dataset. The download may take a few seconds.

<img src="../images/dataset.png" style="border: 2px solid black;">


#### 7. Complete the Onboarding Notebook

- Go back to the *Current Folder* and open the `demo-workspace` directory.

- Open the file `onboarding.ipynb` and complete it by following the instructions in the notebook.

<img src="../images/onboarding.png" style="border: 2px solid black;">

#### 8. Stop Your Server When Finished

- Go to *File* (top left corner) → *Hub Control Panel* → *Stop Server* to shut down your environment when you're done.

<img src="../images/stop-server.png" style="border: 2px solid black;">
