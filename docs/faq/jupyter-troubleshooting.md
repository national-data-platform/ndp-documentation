# FAQ - Jupyter Troubleshooting

This section addresses some of the most common issues users encounter.

### My requirements are not being installed

If you're trying to install requirements from a `requirements.txt` file, make sure you're in the correct path so the install button can detect the file. You must be located in the same directory as the `requirements.txt` file. You can confirm your directory through the *Current Folder* window in the extension.

### My workspace assets were not downloaded

Assets can be downloaded directly using the download button only if they are provided as direct download URLs. Check the catalog entry to confirm this is the case. Otherwise, refer to the information in the asset entry for instructions on how to access it.

### My files were not saved

JupyterHub sessions do not persist files by default. If you need your files to be available across sessions, make sure to save them in either your **user persistent storage** or a **group shared storage**.

### My Python notebook is not reading the directory

Sometimes, when new files are added to a path, the kernel may not detect them, leading to errors when executing a cell in a notebook. Restarting the kernel typically resolves this by refreshing the recognized paths.

### I clicked "Start Server" multiple times and my Jupyter session doesn't seem to launch

NDP's main JupyterHub is hosted by the National Research Platform. As a shared research cluster, it operates on a first-come, first-served basis. If your session isn't launching, one of the following may be happening:

- The cluster is undergoing maintenance.
- There are no nodes currently available to fulfill your request.

### Error HTTP 401: Unauthorized (Your session has expired. Please log out and log in again)

When accessing the JupyterHub site, is possible that you encounter the following message:

<img src="../images/error.png">

When you log in to JupyterHub, you are issued an access token that remains valid for 24 hours. 
To renew your token, simply log out and log back in.

If you are in the JupyterHub landing page, navigate to the top-right corner of the page and click the 
*Logout* button.

<img src="../images/main-logout.png">

If you have an active server running:

1. On the top left, click on *File*
2. Go to the bottom of the dropdown menu and click on *Log Out*

<img src="../images/jhub-logout.png">

**NOTE:** You must log out and log in within JupyterHub, not the main NDP site. If you go to the main NDP site to log out and
log in again, your JupyterHub access token will not be reset. 

!!! tip
    Avoid running processes that may take more than 24 hours to complete. If extended processing time is unavoidable, consider implementing checkpoints to save your progress periodically. Keep in mind that if you start a long-running process and your access token expires during execution, the kernel will terminate, resulting in the loss of any unsaved progress.

### Spawn failed: (422) 

If your server fails immediately after launching, you may see an error like this:

<img src="../images/spawn-failed-422.png">

Check the logs for this message:

```
Invalid value:
\"username/image-name:tag \": must not have leading or trailing
whitespace","field":"spec.containers[0].image"}]},"code":422}
```

This error means your Docker image name has a leading or trailing space. This commonly happens when typing (or pasting) into the image field:

<img src="../images/bring-your-own-image.png">

Clear the image field, retype the image name carefully, and relaunch the server.

#### Workspace files are not downloaded to current folder

When you try to add a dataset to your current folder, it is possible that you encounter the following message:

<div style="text-align: center;">
  <img src="../images/download-failed.png" width="250">
</div>

The issue encountered occurs because the dataset from the catalog lacks valid download links to supported file formats. To ensure successful downloads, the dataset must provide direct links to valid data formats, such as CSV, TXT, TIFF, ZIP, etc. If the dataset includes links to unsupported formats, like HTML pages or shared drive links (e.g., Google Drive, Dropbox), the download process will fail.

Please verify that the catalog contains proper direct links to downloadable files in the supported formats. If these links are not available, consider using an alternative method to upload your data, such as directly uploading it to Jupyter or accessing it through an API.