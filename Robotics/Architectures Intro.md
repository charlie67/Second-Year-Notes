# Architectures

----

[TOC]

## Autonomous Mobile Systems

* Must be able to move around in the real world 
* Must be able to respond to the real world 
* Should be capable of performing tasks and interacting with the world 
* Should be able to survive independently in the world for a period of time
  * Needs to be able to clean solar panels etc..
  * Clean and look after itself in adverse conditions



## Robotics Paradigms

* Reactive
* Deliberative
* Hybrid (combination of the best of both)

### Primitives

* This is how the robot system functions
* If this sensor is pressed then it means the robot has bumped into something
* Plan is data that has been bought in from the robots sensors or information that the robot already knows and has
  * e.g. from a built in model of the world
* 

| Robot Primitives | Input                                  | Output             |
| ---------------- | -------------------------------------- | ------------------ |
| Sense            | Sensor Data                            | Sensed Information |
| Plan             | Information (sensed and/or congnotive) | Directives         |
| Act              | Sensed information or directives       | Actuator Commands  |



### Reactive

* Stems from the mid-80's, although around in other forms before then 
* Originated through researchers looking at biology and cognitive science 
* More accessible due to decrease in hardware costs, and increase in computing power 
* Cheap robots

![](https://images.charlie.to/19-07-00-26-05-18.png)
![](https://images.charlie.to/19-07-13-26-05-18.png)

####Outline
* Based on parallel “behaviours”
* Sensor connected directly to actuator
* Usually a simple arbitration mechanism
* Execute in the cycle time of most natural environments
* No generalised model of the world
* Uses the world as its own model
* Typically lacks a formal mechanism for handling complexity
* Act on interrupts
* Wait for a sensor to tell you what to do 
* Sensor -> little bit of processing -> control a motor
* Don't wait for sensor data to process or the planning system to control what to do next



### Deliberative

![](https://images.charlie.to/19-09-13-26-05-18.png)
![](https://images.charlie.to/19-16-53-26-05-18.png)

* Sensors transmitted directly to the “brain”
* Has a complex representation of the world (a hard
  problem)
* Works out actions using this world model
* Rich planning system needed
* Difficulty in modelling the underlying dynamics and
  uncertainty
* Intelligence is in the planner or the programmer
* Sensor data is transmitted to the brain 
* Which is then processed and based on that it decides where to go and what actions to take

#### Outline

* Emerged in the 90's 
* Decomposes task into subtasks 
* Figures out which are the best behaviours to use to achieve the subtasks 
* Continue as for the reactive paradigm 
* Planner can eavesdrop on the behaviours

### Deliberative vs Reactive

* Deliberative
	 	Not real time 
	 	Enviroment may have changed by the time you've figured out what to do
* Reactive
	* Don't have the same bottleneck
	* Other tings can happen in parrallel 

###Hybrid

* The best of both
* Take in data process some of it but also immediately react to some of it

![](https://images.charlie.to/19-29-44-26-05-18.png)
![](https://images.charlie.to/19-30-16-26-05-18.png)

####Outline

* Decomposes task into subtasks
* Figures out which are the best behaviours to use to achieve the subtasks
* Continue as for the reactive paradigm
* Planner can eavesdrop on the behaviours

