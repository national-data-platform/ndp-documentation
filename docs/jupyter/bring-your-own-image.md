# Bring your own image

The NDP JupyterHub service allows users to bring in their own Jupyter-based images, giving them flexibility and control over their computing environment. Here are three key advantages:

## Understanding Containers, Docker, and Images

[Containers](https://en.wikipedia.org/wiki/Containerization_(computing)) are lightweight, portable environments that package software, 
dependencies, and settings together, ensuring your application runs consistently across different systems.

[Docker](https://www.docker.com/) is a popular tool for managing these containers, making it easier to build, share, and run them.

A Docker image is like a "blueprint" or "recipe" for creating containers. It includes everything your container needs—like libraries, code, 
and configurations—to run a specific application or environment. Once you build an image, you can use it to create containers 
anywhere, from your local machine to cloud servers.

When you launch a server in NDP JupyterHub selecting the default , what happens behind curtains is that an image is used to create a JupyterLab 
with the python minimal setup, plus the [NDP Widget](../jupyter/widget.md).  


**Persist your environments**

By bringing your own Jupyter-based image, you can persist your personalized environments across sessions. 
This ensures that all installed packages, dependencies, and configurations are maintained, making it easy to resume your work without 
having to reinstall or reconfigure the environment each time you launch a new pod.

**Customize multiple kernels**

When you build your customized image, you can configure multiple kernels for different projects. Whether you need specific libraries, 
versions of Python, or other programming languages, you can tailor each kernel to the needs of your project, providing a more 
efficient and organized workflow for working on multiple tasks simultaneously.

**Leverage CUDA-based projects:**

For AI and deep learning projects that require CUDA support, you can bring your own images with the necessary CUDA drivers and configurations. 
This allows you to run GPU-accelerated workloads on the server, which is ideal for resource-intensive tasks such as training machine learning 
models without worrying about compatibility issues with pre-installed CUDA environments.

## Docker 

To be able to setup an image and take the most advantage of it, you will need to familiarize yourself with [Docker](https://www.docker.com/). 

Docker is a system that allows you to create and run applications in a customized environment called 
[containers](https://en.wikipedia.org/wiki/Containerization_(computing)). 
In the back, the JupyterHub service is running a Jupyter Notebook container with minimal configuration. There

## Example

In this example, we are going to use a repository with three demos developed by the team of the [Scientific Computing and Imaging Institute](https://www.sci.utah.edu/) at the University of Utah. 

**1 - Setup Docker**

To install Docker in your system, follow the official [Docker documentation](https://docs.docker.com/engine/install/). 

Make sure to create a [Docker Hub](https://hub.docker.com/) account during your setup. 

**2 - Create the Dockerfile**

In a local folder, write the following [Dockerfile](https://docs.docker.com/reference/dockerfile/).

```
FROM quay.io/jupyter/base-notebook:latest 

WORKDIR /home/jovyan/work

USER root

RUN apt-get update && apt-get install -y \
    git

RUN git clone https://github.com/national-data-platform/jupyter-notebooks

# Install dependencies for Sage
RUN pip install -r /home/jovyan/work/jupyter-notebooks/utah_demos/sage/requirements.txt

# Install dependencies for NOAA
RUN pip install --no-cache-dir -r /home/jovyan/work/jupyter-notebooks/utah_demos/NOAA/requirements.txt

RUN cp -R ./jupyter-notebooks/utah_demos/. . && \
    rm -rf ./jupyter-notebooks && \
    chown -R jovyan:users /home/jovyan/work

USER jovyan
```

In this simple Dockerfile, we have done the following: 

1. We used a Jupyter based image `quay.io/jupyter/base-notebook:latest ` as the base for our custom image.
2. We moved to the working directory, changed to the root user and updated the system. Additionally, we installed `git`.
3. We cloned the National Data Platform repository with the notebooks for three different demos. 
4. We installed the requirements for three demos (Earthscope, SAGE and NOAA).
5. We copied the three notebooks' folders into our working directory and removed the repository, as we don't need the rest of the notebooks.

**3 - Build the image** 

In terminal go to the folder where your Dockerfile is located, and run the following command:

```
docker build -t my-dockerhub-user/demo-image .
```

In the above command, we are tagging the image as *demo-image* (you can use a different tag name), and then we close with a dot to 
indicate Docker to use the current folder as the source of the Dockerfile. Make sure to replace `my-dockerhub-user` with your actual 
Docker Hub username. 

After the image is built, push your image to your Docker Hub repository. 

```
docker push my-dockerhub-user/demo-image:latest
```
The *latest* tag at the end indicates the current version of the image.

**4 - Access JupyterHub and launch a new pod using your image**

Once you have pushed your image, go to [JupyterHub](https://ndp-jupyterhub.nrp-nautilus.io/hub/spawn) and paste the 
image in the **Bring your own image** box (in this case, paste `my-dockerhub-user/demo-image:latest`).

**5 - Execute the demos**

Once your pod is ready, go to your current folder and notice three folders associated with each of the demos. Inside each folder, you
will find a Jupyter Notebook ready for execution.

## List of images

In the following [site](https://quay.io/organization/jupyter), you can consult the full list of images from 
[Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html), which you can use as the base for your custom images.

