# Introduction to Robotics

----
[TOC]

##Differences between Computers and Robots



| Computer                                                     | Robots                                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Input sumbols are static and                                                                                         well behaved | Sensory signals are noisy and unreliable, e.g. IR sensors, sonar, these senors can give different results over different readings |
| Operations give consistent results                           | An action can have different responses                       |
| Enviroment is fixed and repeatable                           | Obejcts may move about indpenedently                         |
| System only recieves intended inputs                         | Influences from external agents can interfere                |
| Perfect performance assumed                                  | Operating enviroment is unreliable, dynamic and incomplete   |



## Robots and the enviroment

* A robot needs different robots to operate on different surfaces

## Intelligent Robotics

* Arkin
  * "An intelligent robot is a machine able to extract information from its environment and use knowledge about its world to move safely in a meaningful and purposive manner”
* Murphy
  * “an intelligent robot is a mechanical creature which can function autonomously”



## Levels of Autonomy

Robots are driven by humans because humans have a much bigger understanding of what they require and what they want to happen

### Remote Control

* A human controlling a robot from a distance
  * e.g. robot wars

### Teleoperation

* Human operator controls a robot from a distance 
* Human cannot physically see the robot 
* Sensors acquire information about the environment 
* Display technology allows the operator to see the sensor data 
*  Communication link available

#### When?

* When the tasks are unstructured and not repetitive
  * When workspace cannot be engineered for industrial manipulator
  * Key portions of the task require dexterous manipulation 
  * Task requires object recognition, situational awareness or other advanced perception 
  * When display technology is rich enough 
  * Availability of trained personnel is not an issue



### Telepresence

* Attempts to reduce cognitive fatigue and simulator sickness 
* Uses virtual reality technology 
* Operator has complete sensory feedback 
* Very expensive in terms of equipment 
* Requires high bandwidth rates 
* One person at least per robot

### Semi-autonomous

* Used a lot in space robotics
  * e.g. Mars Rover

* Continuous assistance 
  * Delegate boring, repetitive control actions to the robot (but still watch over it!)
  * Take over and perform hand-eye coordination tasks 
  * Still requires high communication bandwidth 
* Control trading 
  * Human initiates an action for the robot to complete autonomously 
  * Assumes robot is capable of autonomously accomplishing a task robustly in unexpected situations



### Autonomous

* Nehmzow (2000)‏ 
  * “Weak Autonomy” robots which carry on-board controllers and power supplies 
  * “Strong Autonomy” requires the power of self government 
  * ability to move in its environment to perform a number of tasks 
  * able to adapt to changes in the environment 
  * able to determine its course of action by its own reasoning processes 
  * ability to build internal representations of the world to plan and learn from experience and change its behaviour accordingly

####How to Achieve Autonomoy?

* Artificial Intelligence 
  * Knowledge Representation 
  * Learning 
  * Planning and Problem Solving 
  * Inference 
  * Search 
  * Perception 
* Robotics feeds into AI and vice versa