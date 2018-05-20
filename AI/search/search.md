# Search

------

[TOC]



## Intro to Search

* The problem of search
  * Define the problem
  * Represent the problem spaces
    * Search trees
    * Graphs
  * Find solution by using a search algorithm



* Define the problem
  * Start state(s) 
    * The initial state
  * Goal state(s) 
    * Where you want to get to
  * State space
    * Search space
  * Operators for moving in the state space
    * Successor function or action
  * A function to test if goal state reached
  * A function to measure path cost



#####Start state

* Where is the problem starting from
  * e.g. chess
    * Starting with all pieces in their starting positions on the board

#####Goal state

* The end state
* What you want to achieve
  * e.g. Noughts or crosses
    * Played board with o's or x's as the winner

#####State space

* All legal positions in the generated search tree from start state to goal state
* Generate state space by using goal state
* Covers all possible outcomes at each stage of a search
* e.g. chess
  * A search state might represent a board position

#####Operator for moving in the goal state space

* Used to generate state space
* Moves that are valid in your search space
  * e.g. chess
    * Pawns can move forward either one square or two

##### Function to check if goal state reached

* Something to determine if the goal has been reached

##### Function to measure path cost

* To determine if this path is good or if there is a better one

#### Example function definition

* The chess problem
  * All board assignments give a huge state space
  * $10^{120}$ different solutions
  * Need help in choosing which move to make next because you can't try them all

##### Chess problem definition

* Start state
  * Initial board position
* Goal state
  * Checkmate (optimal) or stalemate
* State space
  * Set of all legal board positions
* Actions
  * Valid position moves
* Goal function
  * Is oppositions king in checkmate or stalemate
* Path cost function
  * Number of moves so far

#### Example route planning 

![Kazam_screenshot_00000](Kazam_screenshot_00000.png)

* Want to start in one position and travel somewhere else using shortest path

###### Problem Definiton

* Start state
  * Arod
* Goal state
  * Bucharest
* State space
  * Set of all possible Journeys (from Arod)
* Actions
  * Valid traversal from any two cities
* Goal function
  * Check to see ig you're at the destination
* Path cost function
  * Sum of the distance travelled



## Representing the problem

* Data structures

  * Trees
    * Binary trees
    * Binary search trees
    * N-ary trees
  * Graphs

  ### Binary trees

  ![](Kazam_screenshot_00001.png)

* Depth of 3

* Each circle is a node (snapshot state)

* Each line is a link

  * Legal move in state space as defined by operators

* Branching factor of 2

  * Because each node has two branches

  ### Binary search tree

  * Either it is empty or each node contains an identifier
  * All identifiers in the left sub-tree are less than the identifier in the root node 
  *  All identifiers in the right sub-tree are greater than the identifier in the root node 
  *  The left and right sub-trees are also binary search trees

###Search trees/N-ary trees 

![Kazam_screenshot_00002](Kazam_screenshot_00002.png)

* Root is null state (or initial state)
* Edges represent one choice
  * Resulting from the operations
* Child states/nodes represent extensions
* Leaf states/nodes are solutions or failures

#### N-ary trees

* A node may have any number of children
* Most problems cannot be represented in a binary tree
* Most problems cannot be ordered for binary search
* Therefore, n-ary trees are usually used to represent search problems

#### Search trees

* Search algorithms do **not** store a whole search tree
  * Would require a **lot** of space
  * Can discard already explored nodes/states in search tree
  * if problem is a graph 
    * i.e. there are loops
      * Then we need to keep track of explored states
* Search algorithms store the frontier of search
  * i.e. the nodes in a search tree with some unexplored children

## Finding a soultion



* Search algorithms are used to find paths through state space from initial state to good state
  * Find ititial (or current) state
  * Check if **goal** found
    * **halt** if so
  * Use operators to expand all next nodes
  * Use search techniques to decide which one to pick next
    * Either use no information (uninformed/blind search) 
    * Or use information (informed/heuristic search)

### Representing the search

* Partial
  * Only store the frontier of search trees
    * Stack
    * Queue
    * Priority queue
* Full
  * Store the whole tree
    * Binary trees/n-ary trees
* A small finite state space can result in an infinite search tree
  * If there is a looping condition
  * This means the problem can't be solved

### The evaluation methods

#### Time complexity

#### Space complexity

#### Optimality

####Completeness