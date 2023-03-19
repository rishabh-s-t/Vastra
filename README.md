# Vastra - Visual Cloth Try On using HR-VITON.
![front-image](./images/front.png)

## Implementation on Colab (Custom Input)
We have implemented the process on Google Colab to try and run the model against custom inputs.
## ![Open In Colab](https://colab.research.google.com/drive/1BTAogr3k3AsTxXaLd4sSSl6HgXfbP5V2?usp=sharing)



## Problem Statement
**Revolutionizing the Clothing Shopping Experience with Advanced Virtual Try-On Technology**
Provide a unique solution that provides clients with a smooth virtual try-on experience for the company's portfolio of clothing. The solution should utilize cutting-edge augmented reality (AR) or virtual reality (VR) technology to deliver an immersive and customized experience that allows customers to imagine how garments appear on them in real-time.

## Our Approach

As we started working on the problem statement, we thought of two plausible solutions.

 - **Solution 1**
	 - Input user's image which they'd like to use for try on.
	 - Use *open-cv* to process the image and extract the facial data of the user.
	 - Use *open-cv* again to super-impose the user's facial data on dummy models. This serves the purpose of a Try-0n.

Soon enough, we realised that this solution is not robust as the user wants to try out the clothes on their bodies than dummy/model bodies. 

- **Solution 2** (*What we implemented*)
We started researching and reading all the available papers and articles about virtual try on.  After skimming through dozens of papers and articles. We came across **HR-VITON**.  
**HR-VITON** is a PyTorch based implmentation of the paper ***High-Resolution Virtual Try-On with Misalignment and Occlusion-Handled Conditions*** by **Sangyun Lee** . It is a Deep Learning model that uses a person's image and a garment's image to generate a synthesized image. This is a 2D approach to the problem of virtual try on. While other approaches focus on the 3D coordinates of the garments and the user. HR-VITON used images to produce results that are effortless. 
HR-VITON is trained on the VITON-HD dataset. **VITON-HD** dataset is a dataset for high-resolution (i.e., 1024x768) virtual try-on of clothing items. Specifically, it consists of 13,679 frontal-view woman and top clothing image pairs.
In our approach, we used **HR-VITON** to produce try on results of various custom inputs of users and garments. 

## Process Overview
![process overview image](./images/process_overview.png)
The task at hand takes 5 steps. 
1. Remove the background from user's input image.
2. Use DensePose to detect the pose in the given image.
3. Use segmentation to differentiate between different sectors of the image.
4. Use PoseNet to generate the pose data of the user. This data is used to calculate the warp of clothing required to properly synthesize both images.
5. Apply segmentation to the cloth image.

All these values are then passed to the HR-VITON model and gives us our required output.


## References
#### HR-VITON
https://github.com/sangyun884/HR-VITON
#### Posenet
https://github.com/rwightman/posenet-python
#### Graphonomy
https://github.com/Gaoyiminggithub/Graphonomy
#### detectron2
https://github.com/facebookresearch/detectron2
#### cloth image segmentation
https://github.com/ternaus/cloths_segmentation
