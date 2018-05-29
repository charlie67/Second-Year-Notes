# Biological Inspired Robots

----

[TOC]

* Robots that resemble living organisms in some way
  * Control system
  * Morphology
  * Actuators
  * Electronics



## Why do we want to use biological inspiration

* Looking for ideas which may give robots 
  * flexibility and agility 
  * novel functionality 
  * the ability to be more adaptive and intelligent 
  * the ability to operate better in human environments

### Degrees of Inspiration

![](https://images.charlie.to/10-44-00-28-05-18.png)

* Loose Metaphors or High Fidelity Replicas?
	*  Can take ideas from the biological world and use these to inspire better engineering designs
	*   Can faithfully model an aspect of biology



## Robots as Biological Models

* Investigate biological questions and test hypotheses 
* Gradually replacing computer models as a tool for embodied cognitive science 
* Becoming accepted by experimental biologists and neuroscientists as tools to validate their models
* Why use a robot as a model? 
  * force scientists to be concrete in specifying the design of a complete 	biological system 
  * help to produce testable hypotheses 
* Robot models allow scientists to study the interaction with the environment (unlike computers) 
* Computer models may introduce simplifications which may misguide the development of the models



## Examples

### Wall Climbing (gecko)

* Useful for surveillance, inspection and cleaning 
* Previous robots have used vacuum suction, magnets, or grasping (all have drawbacks) 
* Want to cling without causing damage 
* Researchers have taken inspiration from the Gecko
* Gecko toe has thousands of filaments (setae) 
* These allow the toe to adapt to any type of surface 
* Exploits forces of weak electrical attraction between molecules to stay attached 
* Operate in both wet and dry 
* Do not require energy
* Uses its tail to balance
* Size and density of the filament very important (not material) 
* Cutkosky at Stanford built an artificial gecko (Skickybot) based on morphological and dynamic properties of gecko's setae 
* Requires method to conform the toes to the surface, and to peel off the foot using foot extension
* Uses biologically inspired materials

### Vision-based Flying Robots

* Environment e.g. search and rescue 
  * cluttered, GPS not available, tele-operation impossible, range-finder e.t.c. not available due to energy consumption and size 
* Vision seen as the most appropriate sensor 
  * small, lightweight 
  * but not trivial to process the information in real time 
* But insects can do it 
  * they use vision to land, take off, search and pursue, and avoid collisions

####Vision-based Flying Insects

* Great deal of biological data available on insect vision 
* 2 compound eyes that span an almost omnidirectional field of view with coarse resolution 
* Several neurons or elementary motion detectors (EMD's) sensitive to the optical flow (motion of animal relative to surroundings) 
* The EMD's have been linked to specific visually guided behaviours

### Vision-based Flying Robots (flys)

* Optical flow is a linear combination of rotation and translation of the animal 
* Translational optic flow is seen as the component for the animal's distance from an object, hence why a fly tends to go in a straight lines separated by rapid turns 
* During turns flies tend to ignore visual information 
* Franceschini et al (1992) used this kind of information to build a physical model of the fly's visual system 
  * mapped visual stimulation into wheeled robot's motor commands
* Signals from two linear cameras pointing sideways detect the magnitude of optic flow 
* A decision is taken from this as to whether to turn 
* The 10kg robot was capable of slaloming through a field of poles at 50 cm/s towards a target location 
* No global map or plan 
* Relied on active behaviours using a combination of attraction to target and repulsion from obstacles

### Wheeled Legs (cockroaches)

* Wheels - allow fast travel on flat terrain 
* Legs – allow movement on rugged terrain 
* Whegs – allow for a combination of both 
* Inspired from cockroach motion 
  * ● used one drive motor 
  * also include jumping whegs 
  * one version included a joint 1/3 of the way down the body for balance when climbing

### Song Recognition and Localisation

* Used a mobile robot to understand how female crickets recognize males' songs and approach them
* Crickets have an ear in each foreleg
*  Enables direction differentiation due to differences in response amplitude
* This turning response does not explain how females can selectively approach males of the same species
* The interval between “chirps” was seen as most important for discriminating different songs
* Theorised that 
  * the sensitivity to the species-specific syllable repetition interval (chirp) depends on specific temporal parameters of the neural circuitry
* Implemented on a Khepera robot with electonic auditory circuit comprising two microphones 
* The robot displayed exactly the same behaviour as observed in the real animals through a simpler mechanism than previously believed

### Vision-based Honing

* Many insects display a remarkable ability to return to nest or to food location after travelling great distances 
* Social insects (ants, honeybees) do this by 
  * path integration
  * visual piloting
* Research into Desert Ants produced a robot based on their behaviour
* Path Integration in desert ants: 
  * achieved by integration of a direction vector computed from the orientation of polarised light in the sky and a distance measurement estimated by step count 
* Path Integration in robots: 
  * achieved by magnetic compass and wheel odometers 
* Both very prone to errors
* Visual Piloting 
  * desert ant seems to use visual cues as it approaches the target location to compensate for path integration errors 
  * this arrived at by experimental observations of the animal behaviour
  * “Snapshot” model assumed (memorise an image and compare to compute a distance vector) 
  * assumes nervous system of ants is capable of memorising an entire image and performing complex comparisons at multiple points on its homing trajectory 
  * does not explain some observed behaviour
* An alternative hypotheses was generated called average landmark vector (ALV) 
* The performance of both models were tested on a robotic platform which was exposed to situations similar to those faced by insects engaged in visual homing 
* In all cases, the ALV model led the robot to the target location with trajectories comparable to those observed in the ants 
* The ALV makes fewer assumptions about the computational and memory load of the animal

