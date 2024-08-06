# NDP Classroom

!!! info
    The following page provides a conceptual overview of the NDP Classroom. The NDP Classroom is currently under development and it's Alpha version is expected to be launched in Fall 2024

The National Data Platform aims to enhance AI learning experience through the NDP Classroom experience. NDP Classroom is designed to support courses that require advanced computational resources for AI-based projects. It provides access to high-performance computing capabilities and a scalable infrastructure, allowing educators and students to tackle complex AI tasks and handle large datasets.

## Features

<img src="images/classroom-flow.png">

This chart is a high level representation of the NDP Classroom experience flow. 

### **NDP Workspace**

The workspace represents the base unit of the NDP classroom. This versatile template allows educators to seamlessly integrate data, models, GitHub repositories, and other essential services. This feature allows for the streamlined setup and launch of projects directly in JupyterHub. 

Instructors can add resources to the workspace such as the following:

- Datasets from [NDP Catalog](https://nationaldataplatform.org/ckandata)
- AI / ML Models (HuggingFace, Model Commons)
- GitHub repositories

### **Groups**

Groups are collaborative instances within a classroom where multiple students working on the same project or class can share a workspace instance. These groups enable students to include additional resources within JupyterHub, such as additional datasets, models or repositories. Each group is provided with shared persistent storage, allowing for collective work and seamless data management. Furthermore, groups can generate a results instance, facilitating the process of compiling and presenting their findings.

### **JupyterHub Service**

The JupyterHub service is the central hub where students perform the majority of their work as part of the classroom experience. It provides a robust environment for coding, testing, and executing AI projects. To enhance functionality, JupyterHub includes three additional extensions:

- [NDP Widget](http://localhost:8000/documentation/jupyter/widget.md): This extension allows students to easily add additional NDP resources such as datasets and models.
- [GitHub extension](http://localhost:8000/documentation/jupyter/github-extension.md): Facilitates the integration of external source code and GitHub repositories.
- [Conda Extension](http://localhost:8000/documentation/jupyter/conda-extension.md): Enables students to manage dependencies and environments within their projects efficiently.


