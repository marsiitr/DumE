# Dum-E Simulation
## Open Projects 2021

***

<p align="justify">
<h2>Simulation</h2>
<p>Dum-E is a pick-up and place, robotic arm. Equipped with image processing and computer vision,it can 
detect and classify objects on the basis of their color or shape. Currently, it can operate in static
environments, that is where obstacles and the object are not moving.</p>
</p>

***


### Object Detection and Classification using Computer Vision
Haar Cascade classifiers are trained on a few hundred sample of images that contain the positive and negative image to identify target object from given images.
The *vision.CascadeObjectDetector* System object detects objects in images by sliding a window over the image. The detector then uses a cascade classifier to decide whether the window contains the object of interest. 
The cascade classifier consists of stages, where each stage is an ensemble of weak learners. The weak learners are simple classifiers called *decision stumps*. Each stage is trained using a technique called boosting. *Boosting* provides the ability to train a highly accurate classifier by taking a weighted average of the decisions made by the weak learners.
Each stage of the classifier labels the region defined by the current location of the sliding window as either positive or negative. *Positive* indicates that an object was found and *negative* indicates no objects were found. If the label is negative, the classification of this region is complete, and the detector slides the window to the next location. If the label is positive, the classifier passes the region to the next stage. The detector reports an object found at the current window location when the final stage classifies the region as positive.
Cascade classifier training requires a set of positive samples and a set of negative images. You must provide a set of positive images with regions of interest specified to be used as positive samples. You can use the *Image Labeler* to label objects of interest with bounding boxes. The Image Labeler outputs a table to use for positive samples. You also must provide a set of negative images from which the function generates negative samples automatically. To achieve acceptable detector accuracy, set the number of stages, feature type, and other function parameters.
#### Code Explanation 
1. Load the positive samples data from a MAT file. The file contains a table specifying bounding boxes for several object categories. The table is exported from the Image Labeler app. 
``` 
load('stopSignsAndCars.mat')
```
2. 

