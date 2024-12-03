# Frequently Encountered Issues

This section addresses some of the most common questions and challenges users encounter.

### My files were not saved

Files are not persistent across sessions unless you save them in your User_Persistent_Storage folder.


### Error HTTP 401: Unauthorized (Your session has expired. Please log out and log in again)

When accessing the JupyterHub site, is possible that you encounter the following message:

<img src="../images/error404.png">

When you log in to JupyterHub, you are issued an access token that remains valid for 24 hours. 
To renew your token, simply log out and log back in.

If you are in the JupyterHub landing page, navigate to the top-right corner of the page and click the 
*Logout* button.

<img src="../images/main-logout.png">

If you have an active server running:

1. On the top left, click on *File*
2. Go to the bottom of the dropdown menu and click on 

<img src="../images/jhub-logout.png">

**NOTE:** You must log out and log in within JupyterHub, not the main NDP site. If you go to the main NDP site to log out and
log in again, your JupyterHub access token will not be reset. 

!!! warning
    Avoid running processes that may take more than 24 hours to complete. If extended processing time is unavoidable, consider implementing checkpoints to save your progress periodically. Keep in mind that if you start a long-running process and your access token expires during execution, the kernel will terminate, resulting in the loss of any unsaved progress.

### Workspace files are not downloaded to current folder

When you try to add a dataset to your current folder, it is possible that you encounter the following message:

<div style="text-align: center;">
  <img src="../images/download-failed.png" width="250">
</div>

The issue encountered occurs because the dataset from the catalog lacks valid download links to supported file formats. To ensure successful downloads, the dataset must provide direct links to valid data formats, such as CSV, TXT, TIFF, ZIP, etc. If the dataset includes links to unsupported formats, like HTML pages or shared drive links (e.g., Google Drive, Dropbox), the download process will fail.

Please verify that the catalog contains proper direct links to downloadable files in the supported formats. If these links are not available, consider using an alternative method to upload your data, such as directly uploading it to Jupyter or accessing it through an API.