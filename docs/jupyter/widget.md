# NDP Widget

The NDP Widget is a JupyterLab extension that provides an interactive interface to access key features of the NDP platform. This widget is accessible from the left menu within the JupyterHub service.

<img src="../images/ndp-widget.png">

The NDP Widget consists of the following components:

- **File Manager:** An alternative access to the file browser, allowing you to manage your files and directories.
- **GIT Extension:** An alternative access to the GIT Extension.
- **Current Folder:** Displays the current folder you are working in, indicating the directory where files will be downloaded or git directories cloned.
- **Install requirements.txt:** Installs a `requirements.txt` file in the current kernel if it exists in the *Current Folder*. A `pip_install.log` file is generated, confirming the successful installation of libraries or indicating any installation failures.

!!! info "Environments are not persistent"
    ⚠️ **Important:** In the current version of NDP, installed libraries and packages are not saved. Each time you return, you will need to reinstall the packages from your `requirements.txt` file before you can start working.

- ***Select your workspace:*** Displays a list of your workspaces and educational modules. Selecting a workspace updates the resources displayed in the following sections.

**NOTE:** If you create a new workspace during a Jupyter session, refresh the dropdown menu to reflect the update.

- ***Add datasets and resources from workspace:*** Displays data and resources associated with the selected workspace. You can choose specific resources and download them to your *Current Folder*. Additionally, you can organize your downloads by selecting the checkbox to automatically create a directory with the name of the dataset, which will contain the downloaded files within your *Current Folder*.

!!! info "Verify your current folder"
    ⚠️ **Important:** In the NDP extension, all selected files will be downloaded to the current folder. If the current folder is not your `User_Persistent_Storage`, your files will be lost when the session ends. To preserve your files, navigate to the persistent storage folder in the file explorer before returning to the NDP extension via the NDP button in the left menu.

- ***Clone GitHub repository into workspace:*** Displays the GitHub repositories associated with the selected workspace. You can choose a specific repository and clone it to your *Current Folder*. 