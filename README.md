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
Basically I aimed to give AI model a 3D building structure and get a flow velocity map image as output. But there were not many reference and slow in speed.
<br>
So I designed novel method to make a simplified input as below. 
<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/5aa0b1c3-e3ca-4f0a-877f-6995e3fe516a">
</p>

Now, Input data is depth map which is 2D, and output is also 2D. 

### Problem Solving 2
Because I have limited computing power, I must limit the mesh numbers while simulating. So there were not enough datas in the image. So I replaced the unallocated grids with the velocity values of the nearest data point with the closest Manhattan distance, as these grids correspond to regions with sparse mesh and low variations in velocity.
<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/fc13d5b4-b057-45c9-8219-c57b53946228">
</p>

### AI Structure
This study requires conducting simulation analysis for each data to provide ground truth labeling, resulting in a very limited number of training data. To overcome this scarcity of data, we employ the UNet architecture, known for its effectiveness in biomedical image processing, which can achieve good results even with limited data. 

### AI Result
I made 3 models with variation in parameters. The results of model1, model2, model3 are shown below. 
<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/ab79951b-c508-4f41-90b9-641cb27f389c">
</p>
<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/780e9b43-2e6b-4b1b-87e1-b76e3b49d97c">
</p>
<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/0565d018-0310-4de6-b15b-8fa317479a60">
</p>

I quantified the validation error of each model using Mean Absolute Error (MAE) and compared them. By comparing the shapes of the flow fields, I decided to use Model 3, which achieved low MAE while accurately predicting the flow field's shape. 

### Application

<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/27d39d74-8639-4151-8052-aaeb4f8974b6">
</p>

From left to right are the Ground Truth velocity image map, the 'building wind damage zone' obtained from Ground Truth data, and the predicted 'building wind damage zone' based on artificial intelligence. While the model hasn't been trained on a large amount of data, resulting in significant errors in areas without buildings, it performed excellently in predicting the 'building wind damage zones' around the buildings. The red areas indicate the 'building wind damage zones.'

### Software Schematic
<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/96f8918c-c904-4ada-942e-d723eb3674bf">
</p>


### AR Views..
For future work, I made a prototype AR model which show a flow field when camera captures a building. Prototype is shown below.
<p align="center">
  <img src="https://github.com/kimthyung/buildingwind_project/assets/98934172/6b02b21c-1b66-4584-a22b-e8e2a6897161">
</p>






