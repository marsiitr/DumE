# Dum-E
## Open Projects 2021

***

<p align="center">
  <img src="https://github.com/rodion0917/Random/blob/main/Dum-E%20in%20Action%20-%20Green%20Object.png">
  <i>Dum-E</i>
</p>

***

<p align="justify">
<h2>Abstract</h2>
<p>Dum-E is a pick-up and place, robotic arm. Equipped with image processing and computer vision,it can 
detect and classify objects on the basis of their color or shape. Currently, it can operate in static
environments, that is where obstacles and the object are not moving.</p>
</p>

***

## Motivation
The name Dum-E, itself is a hint of our source if inspiration for doing this project. After all,who 
hasn't watched Iron Man. Dum-E first appeared in Iron Man I, though it keep messing things for Tony, 
it had saved his life too. 
Our inspiration was simply to make something cool and learn the basics of robotics, computer vision,
image processing and the various platforms which can be used for designing and simulating our robotic arm. 
***

## Workflow


<p align="center">
  <img src="https://github.com/rodion0917/Random/blob/main/Work-flow%20chart.png">
  <i>Workflow</i>
</p>


<p align="center">
  <img src="https://github.com/rodion0917/Random/blob/main/Picking%20up%20the%20object%20-%20Workflow.png">
  <i>Picking up the Object</i>
</p>


<p align="center">
  <img src="https://github.com/rodion0917/Random/blob/main/Placing%20the%20object%20-%20Workflow.png">
  <i>Placing the object</i>
</p>

***
## Software Aspects 
The software aspects in Dum-E are two-fold, namely the control theory and image processing. 
### Control Theory for Dum-E 
After deciding the mechanical aspects of Dum-E, such as DOFs, end-effector workspace and limits for weight lifting, we were left with the control aspects of our project. We tried to figure out how the robotic arm would take an object from a known position and place it at another known position. Fortunately, MATLAB provides a number of useful functions which makes it easy for the user to design the inverse kinematic solver for robotic arm. 
### Object Detection and Classification using Computer Vision
Before using IP, we were only able to perform pick up and place function on a very narrow range of similar shaped and sized objects. Also, we couldn't command Dum-E to place one object at a certain place and then other one at a different position. So to overcome this hurdle, we used Haar Cascade Object Detector, particularly due to the various tools provided by MATLAB which makes this task relatively easy. The Haar Cascade algorithm needs a modestly sized dataset of images to train the Cascade Object detector. This is done using an inbuilt *train* function in MATLAB. After that, through *Boosting* the accuracy and precision of dection and classification is increased. Finally, we were able to make Dum-E perform pick up and place function on differently colored objects and also to place them at different locations.

## Simulation
We had imported KINOVA GEN3 robotic manipulator from solidworks. By using the MATLAB function helperCreateObstaclesKINOVA, we create collision meshes and imported work desks and robotic manipulator to the environment.
The cad Model, [Kinova Gen 3](https://www.kinovarobotics.com/en/products/gen3-robot) is imported directly to be used in the simulation.
To perform the task, Environment is created to place shelves, balls and blocks for the robot so that pick and place task is performed.<br>
The final video for the simulation is in the Images and Video Folder. the simulations are then run to identify the object and place it to<br>
the desired position. The Instructions for the same are below.<br>

### Instructions
Import robot
 ```
 robot = loadrobot('kinovaGen3', 'DataFormat', 'column');
 ```
 [Build World](https://github.com/rodion0917/DumE/blob/main/src/example_Command_Build_World.m) <br>
 This command help create the shelves, blocks and the spheres so that pick and place task can be comnputed.
 
 [Detect Parts](https://github.com/rodion0917/DumE/blob/main/src/example_Command_Detect_Parts.m) <br>
 This function detects parts using a list in the coordinator that also provides the pose.
 
 [Classify Parts](https://github.com/rodion0917/DumE/blob/main/src/example_Command_Classify_Parts.m) <br>
 This step helps classify the parts to determine where to place them.
 
 [Plan Execute Trajactory](https://github.com/rodion0917/DumE/blob/main/src/example_Helper_Plan_Execute_Trajectory_Pick_Place.m) <br>
 This function generates a collision-free trajectory between an initial configuration given by JOINTINIT <br> 
 and a target task-space orientation, provided by TASKFINAL.
 
 [HelperCoordinatorPickPlace](https://github.com/rodion0917/DumE/blob/main/src/example_Helper_Coordinator_Pick_Place.m) <br>
 This class is used to control the pick-and-place workflow execution.
 
 [Activate/Deactivate Gripper](https://github.com/rodion0917/DumE/blob/main/src/example_Command_Activate_Gripper.m) <br>
 This command activates and deactivates the gripper. It has 2 effects:<br>
 1. When the gripper is activated, the picked part is added as a collision mesh to the robot rigid body tree so that path<br>
    planning includes the part in the obstacle avoidance stage. When deactivating the gripper, the placed part is removed <br>
    from the collision meshes of the rigid body tree.
 2. The visualization is updated to move the object being picked up by the gripper. 
 
 [Compute Grasp Pose](https://github.com/rodion0917/DumE/blob/main/src/example_Command_Compute_Grasp_Pose.m) <br>
 This command computes the task-space grasping pose required for the manipulator to pick up a part.

[Move to Task configuration](https://github.com/rodion0917/DumE/blob/main/src/example_Command_Move_To_Task_Config.m) <br>
This command moves the manipulator from its current pose to a desired task-space pose.

[Command Picking logic](https://github.com/rodion0917/DumE/blob/main/src/example_Command_Picking_Logic.m) <br>
This command instructs the robot which parts to pick next based on the order of a preset list.

[Flow chart Pick and Place](https://github.com/rodion0917/DumE/blob/main/src/example_Helper_Flow_Chart_Pick_Place.sfx) <br>


[Time based stace inputs](https://github.com/rodion0917/DumE/blob/main/src/example_Helper_Time_Based_State_Inputs_Pick_Place.m) <br>


## Cost Structure
| *Components*                                                                                                              |*Cost(INR.)*|
|---------------------------------------------------------------------------------------------------------------------------|------------|
| [MATLAB](https://in.mathworks.com/pricing-licensing.html)                                                                 | 62,000     |
| [Simulink](https://in.mathworks.com/pricing-licensing.html?prodcode=SL)                                                   | 94,000     |
| [Model Predictive Control Toolbox](https://in.mathworks.com/pricing-licensing.html?prodcode=MP&&intendeduse=undefined)    | 62,000     |
| [Simscape](https://in.mathworks.com/pricing-licensing.html?prodcode=SS)                                                   | 62,000     |
| [Robotic System Toolbox](https://in.mathworks.com/pricing-licensing.html?prodcode=RO)                                     | 54,000     |
| [Computer Vision Toolbox](https://in.mathworks.com/pricing-licensing.html?prodcode=VP)                                    | 39,000     |
| [Optimization Toolbox](https://in.mathworks.com/pricing-licensing.html?prodcode=OP)                                       | 36,400     |
| *Total*                                                                                                                   | *4,09,400* |

## Applications
Dum-E can be used for multiple industrial applications, from welding, material handling, and thermal spraying, to painting and drilling. With some modest alterations, the end effector of Dum-E can achieve human-like dexterity in a variety of environments. These may include servicing nuclear power stations, welding and repairing pipelines on the ocean floor, remote servicing of utility power lines, or cleaning up radioactive and other hazardous wastes. Of course, we will have to use different type of end effectors for different applications. Tasks which require heavy-lifting will demand suction grippers, whereas more intricate tasks can be accomplished only by using 2-finger or 3-finger electric gripper.
Another example where Dum-E can be used is in the auto-manufacturing industry. Robots have been a boom to the auto-manufacturing industry. Most industrial robots work in auto assembly lines, putting cars together.Dum-E can do a lot of this work more efficiently than human beings because of its speed and relative precision. It also will significantly reduce worker injuries, including repetitive stress injuries and more significant mishaps that can do major harm. Additionally, the robot will turn out a more consistent product at a significantly cheaper cost than can humans.
***

## Limitations 

***

## Future Improvements
In future, we would work on making Dum-E function in a dynamic environment. Also, we try to enable Dum-E as a whole and not just its end-effector to move in dynamic environment. 
***

## Team Members 
1. [Abhay Pratap Singh](https://github.com/DarthEkLen) <br/>
2. [Ayush Mishra](https://github.com/rodion0917) <br/>
3. [Shivshankar Shukla](https://github.com/SHIV-anna) <br/>
4. [Siddhant Shekhar](https://github.com/SiddhantShekhar) <br/>
***

## Mentors
  [Rishika Chandra](https://github.com/chandrarishika14)
***

## References
* [Importing CAD model in MATLAB](https://in.mathworks.com/help/physmod/sm/cad-import.html?s_tid=CRUX_topnav) <br/>
* [Creating predefined Simulink environment](https://in.mathworks.com/help/reinforcement-learning/ug/create-predefined-simulink-environments.html) <br/>
* [Inverse Kinematics](https://in.mathworks.com/help/robotics/ref/inversekinematics-system-object.html) <br/>
* [Tracing End Effector using Inverse Kinematics](https://in.mathworks.com/help/robotics/ug/trace-end-effector-ik-simulink.html?searchHighlight=define%20the%20trajectory&s_tid=srchtitle) <br/>
* [2-D Inverse Kinematic](https://in.mathworks.com/help/robotics/ug/2d-inverse-kinematics-example.html) <br/>
* [Building Robotic Manipulator through rigidBodyTree](https://in.mathworks.com/help/robotics/ug/build-a-robot-step-by-step.html) <br/>
* [Pick and Place Workflow using Stateflow](https://in.mathworks.com/help/robotics/ug/pick-and-place-workflow-using-stateflow.html)
