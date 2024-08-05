# NASA HLS Demo

## Description

The [Harmonized Landsat and Sentinel-2 (HLS)](https://hls.gsfc.nasa.gov) project is a NASA initiative aiming to produce a seamless surface reflectance record from the Operational Land Imager (OLI) and Multi-Spectral Instrument (MSI) aboard Landsat-8/9 and Sentinel-2A/B remote sensing satellites, respectively.

As part of collection of the collection of the [NAIRR Pilot resources](https://nairrpilot.org/pilot-resources), NASA in partnership with IBM has developed [Prithvi-100M](https://huggingface.co/ibm-nasa-geospatial/Prithvi-100M), a temporal Vision transformer pre-trained on contiguous HLS data There are 3 examples of finetuning the model for image segmentation using the mmsegmentation library available through HuggingFace: burn scars segmentation, flood mapping, and multi temporal crop classification, with the code used for the experiments available on GitHub.

The demo covers the use of the model for 3 different use cases:

* An exploration of the raw model, plus a demo for each of the three different fine-tuned cases. 
* A replication of the finetuning for the case of the burn-scars data.
* A guidance on how to set-up a finetuning.

## Start the notebook

1. Sign in to NDP.
2. Once you have signed in, launch JupyterHub.
3. Select the following fields:
    * `Region`: Any
    * `GPUs`: 1
    * `Cores`: 1
    * `RAM, GB`: 16
    * `GPU Type`: NVIDIA GeForce GTX 1080 Ti 
    * `/dev/shm for pytorch`: Select checkbox
    * `Image`: NAIRR Pilot: NASA - Harmonized Landsat Sentinel-2 (HLS) Starter Code
    * `Architecture`: amd64
4. Click on *Start*. Wait for the server to start. 
5. Once you're inside JupyterLab, click on the `hls-foundation-os` folder and open the `exploration.ipynb` notebook.  
6. Follow the notebook instructions. 
7. Once you've completed the demo, you have to stop your server. To do this, go to the left corner and click on *File*, followed by *Hub Control Panel*. 
8. If you're only running the demo server, click on *Stop My Server*. If you're running multiple servers, make sure to stop the right server. 


