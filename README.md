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

## Simulation
We had imported KINOVA GEN3 robotic manipulator from solidworks. By using the MATLAB function helperCreateObstaclesKINOVA, we create collision meshes and 

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
