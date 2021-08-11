# Dum-E Software Aspects
## Open Projects 2021

***

### Control Theory for Dum-E
After creating a rigid body tree model for Dum-E using the rigidBodyTree class, we were able to define all the joint constraints that the solver will enforce. If a solution is possible, the joint limits specified in the robot model are obeyed.
The inverseKinematics System object in MATLAB creates an inverse kinematic (IK) solver to calculate joint configurations for a desired end-effector pose based on the  rigid body tree model. 
To compute joint configurations for a desired end-effector pose:
1. Create the inverseKinematics object and set its properties.
```
ik = inverseKinematics
ik = inverseKinematics(Name,Value)
```

2. Call the object with arguments, as if it were a function.
```
[configSol,solInfo] = ik(endeffector,pose,weights,initialguess)
```
The above function finds a joint configuration that achieves the specified end-effector pose. Specify an initial guess for the configuration and your desired weights on the tolerances for the six components of pose. Solution information related to execution of the algorithm, solInfo, is returned with the joint configuration solution, configSol.

### Object Detection and Classification using Computer Vision
Haar Cascade classifiers are trained on a few hundred sample of images that contain the positive and negative image to identify target object from given images.
The *vision.CascadeObjectDetector* System object detects objects in images by sliding a window over the image. The detector then uses a cascade classifier to decide whether the window contains the object of interest. 
The cascade classifier consists of stages, where each stage is an ensemble of weak learners. The weak learners are simple classifiers called *decision stumps*. Each stage is trained using a technique called boosting. *Boosting* provides the ability to train a highly accurate classifier by taking a weighted average of the decisions made by the weak learners.
Each stage of the classifier labels the region defined by the current location of the sliding window as either positive or negative. *Positive* indicates that an object was found and *negative* indicates no objects were found. If the label is negative, the classification of this region is complete, and the detector slides the window to the next location. If the label is positive, the classifier passes the region to the next stage. The detector reports an object found at the current window location when the final stage classifies the region as positive.
Cascade classifier training requires a set of positive samples and a set of negative images. You must provide a set of positive images with regions of interest specified to be used as positive samples. You can use the *Image Labeler* to label objects of interest with bounding boxes. The Image Labeler outputs a table to use for positive samples. You also must provide a set of negative images from which the function generates negative samples automatically. To achieve acceptable detector accuracy, set the number of stages, feature type, and other function parameters.

#### Code Explanation 
1. Load the positive samples data from a MAT file. The file contains a table specifying bounding boxes for several object categories. The table is exported from the Image Labeler app. 
``` 
load('stopSignsAndCars.mat');
```

2. Specify the folder for negative images and create an imageDatastore object containing negative images. 
```
negativeFolder = fullfile(matlabroot, 'toolbox', 'vision', 'visiondata', ... 'nonStopSigns');
```

```
negativeImages = imageDatastore(negativeFolder);
```

3. Then train a cascade object detector called 'stopSignDetector.xml' using HOG features. 
```
trainCascadeObjectDetector('stopSignDetector.xml', positiveInstances, ... negativeFolder, 'FalseAlarmRate', 0.1, 'NumCascadeStages', 5);
```

4. Now use the newly trained classifier to detect a stop sign in an image. 
```
detector = vision.CascadeObjectDetector('stopSignDetector.xml')
```

5. At last read the test image & detect a stop sign.
```
img = imread('stopSignTest.jpg')
```
```
bbox = step(detector, img);
```
6. Then insert bounding box rectangles and return the marked image. 
```
detectedImg = insertObjectAnnotation(img, 'rectangle', bbox, 'stop sign')
```