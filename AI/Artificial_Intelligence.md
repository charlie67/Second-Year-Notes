* # Fuzzy Logic

  Fuzzy logic is a type of logic that recognizes more than simple true or false values.

  With fuzzy logic propositions can be represented with degrees of truthfulness or falsehood.

  - Traditional Logic is true or false
    - 0 or 1 
    - Can't be in-between

  However, the world isn't black or white, reality isn't that precise

  ##### Greedy(Richard)⊂ [0,1]

  - Richard is either Greedy or he isn't 

  ##### But What if Richard is only somewhat greedy?

  - Fuzzy variables have values in the range of [0,1]
    - e.g. Greedy(Richard) = 0.7
    - King(Richard) = 1

  ## Terminology

  ------

  ##### Universe of discourse

  - Also just called universe
  - The range of values a variable can take
  - e.g. [10, 110] for temperature
  - whatever is appropriate for the application

  ##### Linguistic Terms

  - The 'words' used to describe the concepts over the universe
  - e.g. freezing, cold, cool, warm, hot
  - these become our fuzzy sets

  | Linguistic Variable | Universe of Discourse | Linguistic Terms          |
  | ------------------- | --------------------- | ------------------------- |
  | Temperature         | [-30,30]              | Freezing, cool, warm, hot |
  | Speed               | [0,250]               | slow, fast                |
  | Age                 | [0,120]               | young, middle-aged, old   |

  

  ## Membership Functions

  ------

  ![Membership Functions Representation](membership-functions.PNG)

  ![Membership Functions Representation](membership-functions-2.PNG)

  

  #### Fuzzy Variables

  - Fuzzy linguistic variables are used to represent concepts spanning a particular spectrum/range
    - e.g. Temp{Freezing, Cool, Warm, Hot}
  - Membership function µ 
    - For any fuzzy set A: µ~A~(x)associates each element x with a membership value in [0,1]
      - e.g. fuzzy set warm 
        - if x=22°C µ~warm~(x) = µ~warm~(22°C) = 0.75 

  Consider the fuzzy set Temp{Freezing, Cool Warm, Hot}

  - Degrees of truth of membership
  - For a given x we can find:
    - µ~freezing~(x)
    - µ~cool~(x)

  ![Cool fuzzy set membership](cool-membership.PNG)

  How cold is 2.5°C

  - µ~cool~(2.5°C) = 0.3
  - µ~freezing~(2.5°C) = 0.7

  ###### Where do these number come from?

  It depends on the defined shape of the fuzzy shape

  - Trapezoids are often used

  ## Trapezoidal membership function

  ##### Left Trapezoid

  ![left-trapezoid](left-trapezoid.PNG)

  ###### Case 1: $x<=a$

  - Membership value =  1

  ###### Case 2: $x>=b$

  - Membership value  = 0

  ###### Case 3: $a<x<b$

  - Membership value = $\dfrac{b-x}{b-a}$

  ##### Right Trapezoid

  ![](right-trapezoid.PNG)

  ###### Case 1: $x<=a$

  - Membership value =  0

  ###### Case 2: $x>=b$

  - Membership value  = 1

  ###### Case 3: $a<x<b$

  - Membership value = $\dfrac{x-a}{b-a}$

  ##### Regular Trapezoid

  ![](regular-trapezoid.PNG)

  ###### Case 1: $x<=a$ OR $x >= d$

  - Membership value =  0

  ###### Case 2: $x>=b$ AND $x<=C$

  - Membership value  = 1

  ###### Case 3: $x >=a$ AND $x <= b$

  - Membership value = $\dfrac{x-a}{b-a}$

  ###### Case 3: $x >=c$ AND $x <= $d$

  - Membership value = $\dfrac{d-x}{d-c}​$

  All of these can come down to:

  - $f(x;a,b,c,d) = max(min(\dfrac{x-a}{b-a},1,\dfrac{d-x}{d-c}),0)$

  ##### Alternative Representation

  - Fuzzy sets can be represented in vector notation

    - This is more useful for discrete rather than real valued universe

    - A = (x~1,~µ~A~(x~1~)),(x~2,~µ~A~(x~2~)), (x~3,~µ~A~(x~3~)) ...)

    - Visually this looks like (for a short height set):

      ![](alternative-vector-notation.PNG)

  

  ### Fuzzy Conjunction (AND)

  - A ∧ B = min(A,B)

    ![](fuzzy-and.PNG)

  - µ~A~(x) ∧ µ~B~(y) = min(0.375, 0.75) = 0.375

  ![](and-sets.PNG)

  - When you're using AND you only want the intersecting area

  When using AND on two fuzzy sets they must both have the same universe (range of values)

  

  ### Fuzzy Disjunction (OR)

  - A ∨ B = max (A,B

  ![](fuzzy-or.PNG)

  - µ~A~(x) ∨ µ~B~(y) = max (0.375, 0.75) = 0.75

  ![](or-sets.PNG)

  - When using OR on a fuzzy set you get all of the area

  When using OR the sets must both have the same universe (range of values)

  ### Fuzzy Negation

  - ¬ A = 1-A

  - Models the NOT operator in logic

    ![](not-fuzzy.PNG)

  - µ~¬A~(x) = 0.625

  - µ~¬B~(x) = 0.25

  - The negation of a fuzzy set is composed of all element negations

  ## Fuzzy Inference

  ------

  - Like traditional logic we want to perform inference

    - i.e. drawing conclusions from data
      - IF A then B
      - IF A AND B THEN C

    ### Fuzzy systems: overview

  ![](fuzzy-system-overview.PNG)

  

  ### Mamdani Fuzzy Systems

  - Given a set of fuzzy rules and a new input to classify, the process is:
    - Fuzzification:
      - Find memberships of input(s) to fuzzy sets
    - Rule evaluation (inference):
      - Use memberships to calculate firing strength of rules
    - Composition/defuzzification:
      - Aggregate across the rules to form an output fuzzy set using the firing strength, then obtain an output value(defuzzify)

  #### Setting up the System

  ![](fuzzy-system.PNG)

  - Establish the "fact" base of the fuzzy system 
    - Identify the input and output of the system and fuzzy set names
    - Define appropriate IF-THEN rules
    - Use RAW data to derive membership functions

  #### Example Air Conditioner

  - Define linguistic terms (fuzzy sets) for temperature
    - COLD, COOL, PLEASENT, WARM and HOT
  - The speeds of the motor controlling the fan has the graduations
    - MINIMAL, SLOW, MEDIUM FAST and BLAST
  - The rules are:

  | Rule 1 | IF   | temp is coLD     | THEN | speed is minimal |
  | :----- | :--- | ---------------- | ---- | ---------------- |
  | RULE 2 | IF   | TEMP IS COOL     | THEN | SPEED IS SLOW    |
  | RULE 3 | IF   | TEMP IS PLEASENT | THEN | SPEED IS MEDIUM  |
  | RULE 4 | IF   | TEMP IS WARM     | THEN | SPEED IS FAST    |
  | RULE 5 | IF   | TEMP IS HOT      | THEN | SPEED IS BLAST   |

  

  - The temperature graduations are related to a persons perceptions of ambient temperature

  | Temp (°C) | COLD   | COOL   | PLEASENT | WARM   | HOT    |
  | --------- | ------ | ------ | -------- | ------ | ------ |
  | 0         | **Y*** | N      | N        | N      | N      |
  | 5         | **Y**  | **Y**  | N        | N      | N      |
  | 10        | N      | **Y**  | N        | N      | N      |
  | 12.5      | N      | **Y*** | N        | N      | N      |
  | 15        | N      | **Y**  | N        | N      | N      |
  | 17.5      | N      | N      | **Y***   | N      | N      |
  | 20        | N      | N      | N        | **Y**  | N      |
  | 22.5      | N      | N      | N        | **Y*** | N      |
  | 25        | N      | N      | N        | **Y**  | N      |
  | 27.5      | N      | N      | N        | N      | **Y**  |
  | 30        | N      | N      | N        | N      | **Y*** |

  ##### Where

  - Y - temp value that belongs to set A (0<µ~A~(x)<1)
  - Y* - temp value that is the ideal member of set A µ~A~(x) = 1
  - N - temp value that is not a member of set A µ~A~(x) = 0

  ##### The triangular membership for the fuzzy sets for temperature are:

  | Temp (°C) | COLD   | COOL   |
  | --------- | ------ | ------ |
  | 0         | **Y*** | N      |
  | 5         | **Y**  | **Y**  |
  | 10        | N      | **Y**  |
  | 12.5      | N      | **Y*** |
  | 15        | N      | **Y**  |
  | 17.5      | N      | N      |
  | 20        | N      | N      |
  | 22.5      | N      | N      |
  | 25        | N      | N      |
  | 27.5      | N      | N      |
  | 30        | N      | N      |

  - Cold
    - valid from 0 to 10
    - for 0 ≤ t ≤ 10 
      - $µµ~cold~(t) = \dfrac{-t}{10} +1$
  - Cool
    - valid from 0 to 17.5
      - for 0 ≤ t ≤ 12.5 
        - $µµ~cool~(t) = \dfrac{-t}{12.5} $
      - for 12.5 ≤ t ≤ 17.5 
        - $µµ~cool~(t) = \dfrac{-t}{5} + 3.5 $
  - All based on the linear equation y = ax + b

  ##### Thoughts on this system

  - It is subjective
    - When one person thinks it's cold it might not match what I think is cold
    - Therefore a controller built for them might not be right for me
  - It is tuneable
    - Fiddle with the fuzzy set membership functions to get better performance
  - Fuzzy sets allow for some flexibility here
    - Might not get perfect definitions straight away but will probably be good enough

  ### Fuzzification

  For this module you'll be given the fuzzy sets and rules

  - fuzzification is then just taking the crisp/raw input values and putting these into the fuzzy sets to obtain the membership values
  - The membership values are  used in the rest of the system

  #### Rules

  - Fuzzy rules look like ordinary rules but use fuzzy variables and sets 
    - Temperature = fuzzy variable
    - Cool = fuzzy set
    - Hot = fuzzy set
    - If temperate is cool then ...
    - The system takes a measurement and finds that the current temperature is Cool to degree 0.3… 
  - Fuzzy inference must take into account these memberships and reason using them
    - It evaluates all rules and determines their truth values/memberships
    - If an input does not precisely correspond to an IF-THEN rule, partial matching of the input data is used