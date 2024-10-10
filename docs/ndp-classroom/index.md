# NDP Classroom

The National Data Platform aims to enhance AI learning experience through the NDP Classroom experience. NDP Classroom is designed to support courses that require advanced computational resources for AI-based projects. It provides access to high-performance computing capabilities and a scalable infrastructure, allowing educators and students to tackle complex AI tasks and handle large datasets.

## Features

<img src="images/classroom-flow.png">

This chart is a high level representation of the NDP Classroom experience flow. 

### **NDP Modules**

The NDP modules represent the base unit of the NDP classroom. Modules allows educators to seamlessly integrate data, models, GitHub repositories, and other essential services. This feature allows for the streamlined setup and launch of hands-on activities and assignments directly in JupyterHub. 

Instructors can add resources to a module such as the following:

- Datasets from [NDP Catalog](https://nationaldataplatform.org/ckandata)
- Supporting links to external resources
- GitHub repositories

Information on how to create a NDP Module can be found in this [page](../ndp-modules/module-tutorial.md).

### **Groups**

Groups are collaborative instances within a classroom of multiple learners working on the same project or assignment. These groups enable students to include additional resources within JupyterHub, such as additional datasets, models or repositories. Each group is provided with shared persistent storage, allowing for collective work and seamless data management. 

### **JupyterHub Service**

The JupyterHub service is the central hub where students perform the majority of their work as part of the classroom experience. It provides a robust environment for coding, testing, and executing AI projects. To enhance functionality, JupyterHub includes an [NDP Widget](../jupyter/widget.md): This extension allows students to integrates the resources from their assigned modules to JupyterHub.

!!! info
    The creation and publication of Modules and Classrooms is limited to users with the *educator* role. Such role must be requested at `ndp@sdsc.edu`