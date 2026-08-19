# FAQ - Jupyter Basics

This page addresses some common questions about using the JupyterHub service.

### How do I bring in my Git repository?

The NDP extension, available when launching your server, is the most seamless approach. Select your workspace, then the repository, and click *Clone Repository*. Note that if the repository is private, you'll be asked to provide a Git token.

### How do I bring in my digital assets?

If the digital asset has a direct download URL, the NDP extension is the most seamless approach. Select the resource you want to download, then click *Download Files to Current Folder*. If the asset does not have a direct download URL, you'll need to bring in the resource programmatically or upload it directly to the server using the *Upload File* button.

### How long does persistent storage last?

Persistent storage remains permanent as long as the user stays active. If a user does not launch a server for 6 consecutive months, their storage is reset and all files are lost. This policy is necessary given the platform's limited resources.

### How much persistent storage do I get?

Users get 10GB of persistent storage by default. This quota cannot be increased, as it is provided through the available storage capacity of the National Research Platform.

### Where does my work get saved?

Servers in JupyterHub do not store files by default. To preserve your work across sessions, make sure to place your files or repositories in your user persistent storage directory, or in a team directory if you're working on a project or educational activity.

### Can other programming environments be used in JupyterHub?

Yes. In addition to JupyterLab, users can also work in RStudio and VS Code within their servers. When launching a server, you'll see the corresponding options to open these environments in separate tabs. Keep in mind that only JupyterLab has the extension that links these environments to your workspaces.