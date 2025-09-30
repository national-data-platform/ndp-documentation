# NDP Workspace

The Workspace is a collaborative environment designed to support a wide range of projects, including AI and Machine Learning (ML) workflows, exploratory data analysis (EDA), scientific research projects and educational projects. Each workspace operates within JupyterHub and provides integration with data resources from NDP Data Catalog and external GitHub repositories. 

<img src="../images/workspace-form.png" style="border: 2px solid black;">

## Use Cases

#### Integrated Workflow Development

The workspace is the main unit for assembling and delivering complete research workflows by integrating datasets from the data catalog, source code from GitHub, and connections to computing resources. Researchers use workspaces to combine data, code, and computation in a unified environment, enabling streamlined exploration, analysis, and experimentation.

#### Classrooms and Data Challenges

Within a classroom or data challenge environment, workspaces function as foundational units that support both structured learning and exploratory, project-based activities. These workspaces align with course or data challenge objectives and provide students with interactive, hands-on modules, assessments, and access to curated datasets and computing resources.

As part of the learning experience, students and participants are encouraged to develop their own workspaces. 

As an example see the [Example Data Challenge and Onboarding](https://nationaldataplatform.org/educationhub/datachallenge/learner/4f8f7f38-a86c-4ecf-ba14-9d5e0b00c919). 


#### Community Training

Research groups and agencies that contribute datasets or services to NDP have the opportunity to develop dedicated workspaces designed as demos or tutorials. These workspaces act as practical tools to train the broader community on how to effectively access, process, analyze, and visualize their resources. For example, a workspace might guide users through working with a sample dataset, demonstrating data utilization workflows and showcasing techniques such as live streaming analysis or real-time data visualization, helping users fully leverage the contributed resources in their own work.

## Key Features of the NDP workspace

#### Metadata Form

This form helps users provide all the relevant information about their workspace, including a clear description, step-by-step execution instructions for running it in JupyterHub, any prerequisites (for educational purposes), tags to improve discoverability, and links to additional resources or references.

#### Data from NDP Catalog

The workspace supports the addition of data resources from the NDP data catalog, making it easy for users to find and utilize datasets relevant to their project. 

#### Models Integration

Users can integrate models from open-source platforms like HuggingFace to enrich their workspaces with advanced machine learning capabilities.

#### GitHub Integration

With GitHub integration, the workspace allows users to connect to external repositories, ensuring that source code, configuration files, and dependencies are easily managed. 

## JupyterHub

[NDP JupyterHub](https://ndp-jupyterhub.nrp-nautilus.io/hub/spawn) service (hosted by NRP's [Nautilus](https://dash.nrp-nautilus.io/)) allows users to develop their workflows in a user-friendly environment.

### NDP Widget
The NDP Widget is a JupyterLab extension that provides an interactive interface to access key features of the NDP platform. This widget is accessible from the left menu within the JupyterHub service.

The NDP Widget consists of the following components:

- **File Manager** 
- **GIT Extension**
- **Current Folder:** Displays the current folder you are working in, indicating the directory where files will be downloaded or git directories cloned.

- **Select your workspace:** Displays a list of your workspaces and educational modules. Selecting a workspace updates the resources displayed in the following sections.

- **Clone GitHub repository into workspace:** Displays the GitHub repositories associated with the selected workspace. You can choose a specific repository and clone it to your *Current Folder*. 

- **Install requirements.txt:** Installs a `requirements.txt` file in the current kernel if it exists in the *Current Folder*. A `pip_install.log` file is generated, confirming the successful installation of libraries or indicating any installation failures.

!!! info "Environments are not persistent"
    **Important:** In the current version of NDP, installed libraries and packages are not saved. Each time you return, you will need to reinstall the packages from your `requirements.txt` file before you can start working.

- **Add datasets and resources from workspace:** Displays data and resources associated with the selected workspace. You can choose specific resources and download them to your *Current Folder*. Additionally, you can organize your downloads by selecting the checkbox to automatically create a directory with the name of the dataset, which will contain the downloaded files within your *Current Folder*.

### User_Persistent_Storage

Once JupyterHub is launched, you will notice a `_User-Persistent-Storage_` directory. This directory corresponds to your persistent storage. Make sure to save your work in this directory, otherwise it will be lost when you disconnect from your server.

Every user is given a **10GB storage**. If you need more space, contact `ndp@sdsc.edu`. 