# Landslide-Prediction-
The Project titled 'Landslide Prediction using Deep-Learning Frameworks and WSN' compares two methods for landslide prediction.

In this project I utilized satellite images from landslide4sense dataset from IARAI [https://www.iarai.ac.at/landslide4sense/challenge/] and performed mapping using a deep learning based image segmentation model U-Net to detect landslides and make predictions on unseen data.

For the second method, I collaborated with two other grad students and designed a sensor network with multiple working nodes, to sense the soil moisture and movement in real-time in a given area for landslide prediction. The process of data collection from these sensors to the base station was also studied. 

Comparative analysis, results, advantages, and shortcomings of landslide prediction using the above-mentioned methodologies are reported in IEEE format.

## Motivation:

Landslides are prevalent disastrous events that pose a major hazard to people and property in populated areas.

The information about occurrence of a landslide can help prevent extensive damage and alert people to take precautionary measures. 

## Data Pre-processing:

Ghorbanzadeh et al [1] have introduced Landslide4Sense as the benchmark for landslide detection. They have used 3,799 image from the Sentinel-2 satellite and ALOS PALSAR. The dataset has been collected from four different times and geographical locations: Iburi (September 2018), Kodagu (August 2018), Gorkha (April 2015), and Taiwan (August 2009). 

Training data consists of 3799 images of size 128 by 128 pixels and of channel width 14 bands and the mask labels associated with the images are of the size 128 by 128 pixels. 

We have also calculated the normalized difference vegetation index (NDVI), which is a standard index that is used to specify the relative biomass of an area. 

Out of all the 14 bands we have chosen red, green and blue colour bands slope and elevation from ALOS PALSAR, the newly calculated NDVI index for our analysis.

<img width="446" alt="image" src="https://user-images.githubusercontent.com/106268058/228088500-b681e135-f9af-4fcf-98f8-053eaa921d87.png">
<img width="451" alt="image" src="https://user-images.githubusercontent.com/106268058/228088535-425dc303-8d7d-4005-99f7-20697ba27173.png">
Fig: data with label example after preprocessing (a) with presence of landslide (b) no presence of landslide

we can see from the above images that if there is a landslide occurrence it will be marked in the corresponding mask label and if there is no landslide in the image the corresponding mask label will be empty.


## Landslide prediction using U-Net deep learning model:

There are many deep learning-based image segmentation models that are essentially based on the architecture of convolutional encoder decoder, of which I have chosen to utilize U-Net. 

The network is modelled according to the original U-Net architecture specifications, with the difference that kernel initializer (the method using which weights are updated) has been specified to be he_normal i.e., it draws the weight samples from a truncated normal distribution centered at zero. The performance of the model greatly improved after using the kernel initializer. 

## Result:

The model has been trained for 20 epochs, and the resultant Precision = 78.3%, and F1 score = 67.9%.

After evaluating the model on the training dataset, we can see that the predictions made by the deep learning model are very close to the actual prediction maps. 

<img width="353" alt="image" src="https://user-images.githubusercontent.com/106268058/228089023-0151ab71-416e-4aa3-bbaf-0a02f59c667f.png">
<img width="357" alt="image" src="https://user-images.githubusercontent.com/106268058/228089034-8ccaddfe-9db6-4ef9-851e-1d68fed6feb3.png">
Fig: predictions made by U-net model compared to actual labels of image

## References:
[1]. Ghorbanzadeh, O., Xu, Y., Ghamis, P., Kopp, M., & Kreil, D. (2022). Landslide4Sense: Reference Benchmark Data and Deep Learning Models for Landslide Detection. arXiv preprint arXiv:2206.00515.








