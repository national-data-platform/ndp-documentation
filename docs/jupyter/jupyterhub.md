# NDP JupyterHub

[NDP JupyterHub](https://ndp-jupyterhub.nrp-nautilus.io/hub/spawn) service (hosted by NRP's [Nautilus](https://docs.nationalresearchplatform.org/userdocs/jupyter/jupyterhub-service/)) allows users to develop their workflows in a user-friendly environment.

## Set Up
!!! info
    Prior to initiate your server, you can consult the [availabe resources page](https://portal.nrp-nautilus.io/resources)
Once in the Hub, you can set up your server by selecting the following fields:
    
    * Region
    * GPUs
    * Cores
    * RAM, GB
    * GPU Type 
    * /dev/shm for pytorch
    * Image
    * Architecture

!!! warning
    Make sure to not reserve an unnecesary amount of GPU's to avoid wasting resource(s). 

## User_Persistent_Storage

Once JupyterHub is launched, you will notice a `_User-Persistent-Storage_` directory. This directory corresponds to your persistent storage. Make sure to save your work in this directory, otherwise it will be lost when you disconnect from your server.

Every user is given a 50GB storage. If you need more space, contact `ndp@sdsc.edu`. 

## Stoping your server

Once you have finished your work, make sure to **stop your server:**

1. On the top left, click on *File*, followed by *Hub Control Panel*.
2. If you're only running one server, click on *Stop My Server*. If you're running multiple servers, make sure to stop the right server.
