# NDP Workspace

The Workspace is a collaborative environment designed to support a wide range of projects, including AI and Machine Learning (ML) workflows, exploratory data analysis (EDA), scientific research projects and educational projects. Each workspace operates within JupyterHub and provides integration with data resources from [NDP Data Catalog](../ndp-catalog/index.md) and external GitHub repositories. 

## Use Cases

#### Integrated Workflow Development

The workspace is the main unit for assembling and delivering complete research workflows by integrating datasets from the data catalog, source code from GitHub, and connections to computing resources. Researchers use workspaces to combine data, code, and computation in a unified environment, enabling streamlined exploration, analysis, and experimentation.

#### Classrooms and Data Challenges

Within a classroom or data challenge environment, workspaces function as foundational units that support both structured learning and exploratory, project-based activities. These workspaces align with course or data challenge objectives and provide students with interactive, hands-on modules, assessments, and access to curated datasets and computing resources.

<img src="../images/data-challenge-example.png" style="border: 2px solid black;">

As part of the learning experience, students and participants are encouraged to develop their own workspaces. 

As an example see the [Example Data Challenge](https://nationaldataplatform.org/educationhub/datachallenge/learner/4f8f7f38-a86c-4ecf-ba14-9d5e0b00c919). 


#### Community Training

Research groups and agencies that contribute datasets or services to NDP have the opportunity to develop dedicated workspaces designed as demos or tutorials. These workspaces act as practical tools to train the broader community on how to effectively access, process, analyze, and visualize their resources. For example, a workspace might guide users through working with a sample dataset, demonstrating data utilization workflows and showcasing techniques such as live streaming analysis or real-time data visualization, helping users fully leverage the contributed resources in their own work.

<img src="../images/community-training.png" style="border: 2px solid black;">

You can discover the publicly available workspaces under [Community Resources](https://nationaldataplatform.org/educationhub/explore?tab=workspaces).

## Key Features of the NDP workspace

#### Metadata Form

This form helps users provide all the relevant information about their workspace, including a clear description, step-by-step execution instructions for running it in JupyterHub, any prerequisites (for educational purposes), tags to improve discoverability, and links to additional resources or references.

#### Catalog Assets

The workspace allows users to easily find and utilize relevant digital assets, such as datasets and models, from the NDP Catalog. 

#### Workspace Codebase

With `git` integration, the workspace allows users to connect to external repositories, ensuring that source code, configuration files, and dependencies are easily managed. 