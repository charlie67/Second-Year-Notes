# Deliberative Systems

----

[TOC]

## Outline

* Sensors transmitted directly to the “brain” 
* Has a complex representation of the world (a hard problem!) 
* Works out actions using this world model 
* Rich planning system required 
* Difficulty in modelling the underlying dynamics and uncertainty 
* Intelligence is in the planner or the programmer

![](https://images.charlie.to/16-18-07-27-05-18.png)

* You're figuring out do you need that interaction from the real world and if so how do you incorporate that into your model and plan


##What do we Need?

* Sensory Input
  * Sensors to see what has been happening and what is currently happening
* Internal Representation
  * World Model
  * Reasoning System
  * Planning Action Sequences
  * Plan Checking
* Execution of the action
  * Robot Programming



## Internal Representation

* Need to be able to reason about things that the
  system already knows
* Deduce answers to problems
* Respond to new situations
* Learn about new facts
  * When it approaches a new situation it should learn about that  situation so if it encounters a similar one in the future it knows what to do and can successfully solve that problem again
* Need
  * appropriate notation (effectiveness)
  * sufficiently precise notation
  * flexibility (coverage)
  * manipulation (reasoning)

###World Model

* To construct an internal model of the world you need:
  * Geometrical properties of the world
  * Physical properties of the world
    * This can be data from the robots sensors 
      * Send the robot around the world and build a model of how the robot sees the world in a way that it understands
  * A representation of the state of the world
  * A reasoning system to move between states of the world



#### Assumptions

* The world is...
  * an accurate reflection of the real world
  * sufficient representation of the real world
  * a complete description of the real world (more commonly called the closed world assumption)
* But...
  * a model is always an abstraction of the real world
  * the real world is not closed
    * Unexpected things can come in and change your enviroment
  * world models are hard to build, maintain and process
  * these are time consuming, precise and greedy operations



#### Reasoning About the World

* Knowledge Representation 
    * Declarative (Logic Systems, Networks)
    * Imperative (Procedural)
    * Hybrid (Frames, Production Systems)



##### Declarative Representations - Logics
![](https://images.charlie.to/16-48-06-27-05-18.png)
![](https://images.charlie.to/16-48-21-27-05-18.png)

* Can enquire: (inside tray oven)? to get an anwer

######Advantages

* Simple economical notation (Maths)
* Solid foundation
* Inference mechanism for info retrieval and problem solving
* Can be extended to represent time/space/ intention etc

######Disadvantages

* No inherent organisation – this can be added but extra work
*  Possibility of enormous processing load
* Not easy to formulate procedural or heuristic rules


##### Declarative Representations: Semantic Nets
![](https://images.charlie.to/17-09-20-27-05-18.png)

* Collection of nodes and links between the nodes
* The representation itself could mean anything
* It is the grounding in the real world that is important
* Have loads of items and links between them are the actions thoses items can do

###### Advantages

* Easy to follow access paths and easy to understand
* Grouped associations (indexing)
  * Allows faster retrivals of facts
* Inheritance gives conciseness to the representation
* Hierarchies possible (in logics, facts all at one level)

###### Disadvantages

* No standard terminology (invent your own!)
* No temporal structure
* No standard inferencing (although semantic nets can be turned into a logic representation for inferencing)



##### Imperative Representation: Procedural

* Follow a precdure (receipe)
* Give instructions on what to do, how long for and in what order
* MAIN:
  * PLACE COMPONENT-A ON TRAY
  	 PLACE COMPONENT-B ON TRAY	
  * PLACE TRAY INSIDE OVEN
  * WAIT 15 MINS
  * REMOVE TRAY FROM OVEN
* PLACE:
  * OPEN GRIPPER
  * MOVE TO 1st ITEM LOCATION
  * CLOSE GRIPPER
  * MOVE TO 2nd ITEM LOCATION
  * OPEN GRIPPER
  * MOVE TO RESET LOCATION
* Robot programmer is involve with operations that cause the desired state of the system
* These contain knowledge but in an  imperative form
  * Imperate - how to do it 
* ● Instructions and recipes give some sequencing information 
* Time intervals can be included 
* Not easy to envisage the total system state at any particular point 
* Relation to other (global) facts not clear 
* The total system state can be hard to decide



### Planning 

####Planning Action Sequences

* Planning is the process of looking ahead at the outcomes of possible actions 
* Search for sequence of actions which will reach the desired goal 
* Uses the knowledge represented in the system 
  * can use any of the many available search strategies from uninformed to heuristic - depends on the problem! 
* Can be very slow
* How to get from city A to city B
* Look ahead and see the advantages and drawbacks of each path to take

#### Planning 

* It is usually necessary to represent the world as a series of states 
* The search is then performed to find a path that will take the robot from the current state to the goal state 
* If you want to find the optimal solution, this may take a long time (so what does the robot do in the meantime?) 
* Various specific optimising methods available 
* lumping connected corridors together etc 
* A limit to what can be done in real time

##### Only Useful if

* the environment does not change during the execution of the plan in a way that affects the plan 
* the robot knows the state of the world and of the plan at all times 
* the robot's effectors are accurate enough to execute each step of the plan in order to make the next step possible
* The robots sensors and programming need to be capable enough to make the plan work

#### Drawbacks

- Time-scale – inputs from sensors, internal models and representations tend to provide a large state space to search – so can take a while 
- Space – large amount of memory may be required both for the internal representation and for the search 
- Information – assumes the information held in the plan is accurate and up to date, if the world has cahnged since the robot has calculated its plan than the plan may be useless and the robot may be unable to do what it wants to do

#### Path Planning

* Many different methods available 
  * Visibility Graph 
  * Penalty Function 
  * Configuration Space

#####Visibility Graph
![](https://images.charlie.to/18-30-01-27-05-18.png)

* Instead of mapping the world accurately and working out a path step by step, shrink the robot to a point and connect points around the start and end verticies of the object, then search that graph using AI techniques
* Robot is shrunk to a point (not a particularly valid assumption!)
* Connect paths from all vertices of the object, start and goal
* Search graph using AI techniques
* The robot does have dimensions so it may end up not fitting and hitting objects

#####Configuration Space
![](https://images.charlie.to/18-32-30-27-05-18.png)

* Increase size of obstacles so they cover an area of space that the robot cannot enter
* Shrink the robot to a point and construct visibility graph
* Can deal with all shapes of robot by overestimating area around obstacles
* Exapnd any obstacles by the dimensions of the robot
* Brings the uncertanty of the real world into the planning of the robot
* Don't make the expansion too big otherwise the robot won't be able to fit

#####Penalty Function
![](https://images.charlie.to/18-34-11-27-05-18.png)

* Direction vector constantly computed
	* attracted to goal, repelled by obstacles
* Can be combined with Configuration Space to
enable robust navigation

##### Reality

* In reality, this works well if you only want to move the robot around 
* If you want the robot to perform completely autonomously, you also need to plan for the manipulation of objects 
  * Grasp Planning
  * Fine Motion Planning

#####Grasp Planning
![](https://images.charlie.to/18-43-16-27-05-18.png)

* Need to consider
  * Safety
  * Reachability
  * Stability
  * Certainty
* Assemble possible grasp points

#####Fine Motion Planning
![](https://images.charlie.to/18-47-37-27-05-18.png)

* Naïve and clever strategies
* Uncertainty and variation present
* Pick a strategy for the current task

######Fine Motion Planning - C Space
* Need more sophisticated approaches
* Convert to c-space and solve using path planning



#### Failure Handling

* Very important as most deliberative systems assume ideal world 
* Deals with uncertainty and variation in the environment and robot
* Main methods are: 
  * Error Detection and Recovery 
  * Worst Case Analysis



##### Error Detection and Recovery

* Notice that something is wrong 
  * Monitoring 
* Identify in what way it differs 
  * Diagnosis 
* Identify how to overcome the deviation 
  * Recovery



###### Monitoring

* Involves the use of sensors to 
  * confirm everything is working correctly 
  * to detect errors 
  * If your sensors aren't working correctly then this part won't work properly
  * So you may need some kind of redundancy 
* In some cases it is difficult to identify the problem or the cause 
* Knowledge must be available to interpret the data 
* Modelling system must keep a track of what is occurring in the real world

###### Diagnosis

* A series of symptoms is analysed in order to reason about the cause of a particular error state
* Often necessary to decide what has actually
  happened
* Level of diagnosis difficult to determine
* Sensor readings are extracted from the context in which they occur
* Enough information must be transferred with the sensor readings to make the diagnosis

###### Recovery

* A recovery plan is formulated and executed in order to repair or correct the diagnosed errors 
* How do we repair the situation? 
* What actions should now be taken? 
  * Prepackaged (CBR?) 
  * Generalised (e.g. clear all) 
  * Planning based 
    * replan from current state 
    * go back to previously correct state 
* Not an easy problem

###### Summary

* Allows errors to occur 
* Attempts to prevent error situations by diagnosis and recovery

##### Worst Case Analysis

* Tries to guarantee that a plan will succeed
* Much use is made of both modelling the workcell and mathematical analysis of the task
* Uses some work we have already seen
	* Fine motion planning
	* Using EDR strategies in Configuration Space

##### Avoiding The Issue

* Attempts have been made to “engineer out” the
unpredictability and error
* Choosing simple and constrained tasks
* Engineering out the potential variability in the task
* Designing the environment for the robot
	* parts designed for robot assembly
	* smoothed paths and tracks
	* vehicles follow paths (lines, tracks, smells)

##### Modelling the Mechanics

* Grasp strategies which are specifically designed to bring the part into a unique orientation and position in the gripper
* Using “fences” to manipulate parts in order to achieve a final known orientation

##### Summary

*  Assumption again that all the knowledge for the analysis is available
* Accurate and up-to-date model is again required
* Small variations in the external world may cause failure of the task
* Reject many strategies which may in the real world correctly perform the assembly
* This leads to inefficient strategies and the systems also consider many situations which will never occur