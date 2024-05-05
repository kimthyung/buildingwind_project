# Prediction of Wind Fence placement for building wind by CFD based Artificial intelligence

Applied Fluid Dynamics Course Final Project, Yonsei University

### Introdiction

The increasing trend of skyscraper construction and higher urban density has led to the recognition of building-induced wind as a new hazard. This study focuses on "wind fences" as a solution to mitigate building-induced wind. By leveraging Computational Fluid Dynamics (CFD) data, AI models are trained to provide optimal wind fence positions quickly, omitting the time and cost-intensive CFD analysis process. 
These solutions can be easily and rapidly applied in the building design phase, presented in the form of Augmented Reality (AR) solutions.

### CFD Datasets
Simulated with ANSYS FLUENT. Random cluster set of CAARC buildings(over 50 cases), under condition below.

<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/012ba634-af72-4974-af0e-d3320a7a473d">
</p>

### Example of CFD Datasets
<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/a799d31b-5112-45ac-9b7e-4d96f765894d">
</p>


### Data Preprocessing
Separated the flow velocity data from CFD results, up to a height of 3 meters above ground.<br>
And remove every z components to make it flat

<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/4fb5e3e1-f7a0-48f7-bc16-6d538cc6b31e">
</p>

To facilitate equal comparison of the datasets, I created a unit grid to easily compare different CFD results. <br> Below is the process of optimizing the grid size.
<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/efcc0701-b793-4b95-a510-88cd75b927ef">
</p>

Based on indicators, I chose an optimal grid as 2m*2m grid in this research 

### Problem Solving 1
Basically I aimed to give AI model a 3D building structure and get a flow field image as output. But there were not many reference and slow in speed.
<br>
So I designed novel method to make a simplified input as below. 
<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/5aa0b1c3-e3ca-4f0a-877f-6995e3fe516a">
</p>

Now, Input data is depth map which is 2D, and output is also 2D. 

### Problem Solving 2
Because I have limited computing power, I must limit the mesh numbers while simulating. So there were not enough datas in the image. So i 

