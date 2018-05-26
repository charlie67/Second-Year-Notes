# Manipulators and Grippers

----

[TOC]

## Parts of a manipulator

![](https://images.charlie.to/20-00-46-24-05-18.png)

* The arm which is amde up of joints and links
* The wrist which can provide more degrees of freedom to your robot
* The arm gets you to a point in 3D space
* The wrist performs the rotations

### The Arm
![](https://images.charlie.to/20-02-59-24-05-18.png)

* A link connects the joints
* Each link provides a degree of motion
* Each joint provides a degree of freedom
* A robot with three links and three wrist motions will have 6 degrees of freedom (which is the maximum)
* You can only have 6 degree of freedom but can have many more degrees of motion
* The degrees of motion is generally the number of links you have

####Arms: Joints
![](https://images.charlie.to/20-08-46-24-05-18.png)
![](https://images.charlie.to/20-08-17-24-05-18.png)

#####Prismatic
* Move in and out

#####Revolute
* Rotation joint in one degree

#####Screw
* In and out
* Moving along one axis

#####Planar
* Can move in two directions x and y

#####Cylindrical

* Can move up/down and around the cylinder 

##### Spherical

* Joysticks



#### DOF vs DOM

![](https://images.charlie.to/20-12-44-24-05-18.png)
* The degrees of freedom (DOF) for these is the same
* But the degree of motion (DOM) is very differnet
* A robot system can have a maximum of 6 independent DOF but an unlimited number of DOM
* DOF is not always the number of joint



#### Arms Classification

* For movements in 3D one needs at least 3 DOF and 3 DOM
  * An arm with 3 links and 3 joints 
    * If 1 DOF joints are used

##### Common Joint Combinations

| Type of arm           | prismatic/linear | revolute/rotary |
| --------------------- | ---------------- | --------------- |
| Cartesian geometry    | 3                | 0               |
| Cyclindrical geometry | 2                | 1               |
| Spehrical geometry    | 1                | 2               |
| Articulated geometry  | 0                | 3               |



##### Cartesian Geometry Arm

![](https://images.charlie.to/20-22-36-24-05-18.png)

* 3 prismatic joints 
* Good repeatability 
* Straight line motion easy 
* Resolution equal and constant over whole workspace
* Typically strong
* Generally have something connected to the ceilng and it can move very big hefty pieces

##### Cylindrical Geormetry Arm
![](https://images.charlie.to/20-26-38-24-05-18.png)

* 2 linear, 1 rotary joint
  * Can go up and down the pole
  * Round the pole 
  * The arm can move in and out
* Resolution depends on extension of the arm
  * Not so easy to control something when the arm is extended 
  * If it's bought in then it's a lot easier to control
* High speeds due to base rotation 
  * Rotary joint is typically very fast
* Inertia can be a problemn



#####Spherical Geometry Arm
![](https://images.charlie.to/20-30-23-24-05-18.png)

* 2 rotary, 1 linear joint
* Two axis of low variable resolution
* Fairly flexible (can reach below the base)
* Complex control algorithms

#####Articulated Geometry Arm
![](https://images.charlie.to/20-30-55-24-05-18.png)

* Resolution depends on arm position
  * Good resolution if you're up close and controllable
  * Out at the extremes you don't have the same level of control
* Accuracy poor
* Repeatability good
* Excellent flexibility
* Complex control
* There has to be motors in each joint or have motors in the central column with links
  * All this adds weight
  * Less weight if the motors are in the centra column



#### Beyond the 3 Joints

* Parller linkage allows for higher load capacity
* Fast motion
* High stiffness
* Direct drive
* Each joint goes in and out
* Can have very big things on 
* More degrees of motion
* Allows more flexibility in movement
* Can move round corners and through bendy pipes
* Allows redundancy

#### Kinematics

#####Direct Kinematics
![](https://images.charlie.to/22-20-22-24-05-18.png)

* Direct kinematics is going from joint space to cartiesian space
* Typically how it works is the user inputs a point in space in x,y and z co-ordinates and using inverse kinematics the program returns the joint movements necessary to go to that point 

#####Inverse Kinematics
![](https://images.charlie.to/22-23-05-24-05-18.png)
* Inverse kinematics is going from cartesian space to joint space
* Sometimes there is no way for the arm to move to that point and sometimes there are multiple solutions
  * The robot needs to know which one is more appropriate

#### Wrists

* The wrist needs to be abke to go around the x,y and z axis
* The arm goes to a position in 3D space the wrist needs to go around that in 3D space

![](https://images.charlie.to/22-29-29-24-05-18.png)
![](https://images.charlie.to/22-29-49-24-05-18.png)

####Grippers

* Most grippers are powered so they can actually accomplish they're tasks

#####Electromagnetic
* Simple to build 
* Can pcik up the wrong things
	* Dirt
	* Rubbish
* Is the only one capable of seperating out layers of cloth


#####Vacuum
* Suction cups 
* Simple and cabling easy
* Gentle on components
* Reliable 
  * Even for heavy weights

##### End of Arm Tooling

* Typically called end-effectors
* Take to from of grippers and tools
* Typically attached to the wrist
* Chosen and designed for particular tasks

#####Fingers
* 2 fingers (open/close)
* More than two fingers is more complex to control but offers greater flexibility
* non-parallel can have self-aligning pads



#### Hands 

##### Morphology and Sensing

* Focus
  * Flexibility and tactile sense
* More the integration of both
* Special role for the thumb
* Challange to find the balane between functionality and weight



##### Control

* Remote
  * Wear a glove that uses your hand to mimic the robots hand
* Very dificult
* Usually pre-programmed with respect to known objects
* Tactile sensors are not the driving force



## Summary

* Manipulator: arm, wrist and end-effector 
* 4 different arm geometries 
* Manipulators act in the 6 dimensional space (DOF vs. DOM) 
* Inverse and direct kinematics 
* Many different kinds of end-effectors


