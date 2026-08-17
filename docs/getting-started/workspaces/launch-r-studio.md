# R Studio

R Studio can be deployed through the JupyterHub service by selecting the pre-built image. When setting up your server, select `Minimal NDP Starter Jupyter Lab + R Studio`. 

<img src="../images/r-studio-image.png" style="border: 2px solid black;">

Once your server is running, select RStudio from the launcher window. This will open a new tab with the RStudio interface, ready for you to begin your work.

Please note: the NDP Widget is not available within the RStudio environment. To continue using the Widger features, keep your JupyterLab session open in a separate tab or window.

As with all Jupyter-launched servers, packages installed within RStudio are not persistent. Any packages you add during a session will be lost once the server is stopped. To ensure reproducibility and persistence:

- Maintain a list of required packages within your project (e.g., requirements.R or a project-specific script).

- For long-term use, consider creating a customized Docker image that includes all necessary R packages pre-installed.
