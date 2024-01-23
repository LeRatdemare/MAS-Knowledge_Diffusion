# Netlogo : notes

## Agents

### Turtles

* Have positions in the World
* *xcor* and *ycor* are not necessarily integers, turtles can be anywhere in a patch

|  Procedure/Variable | Description |
|  --------- | ----------- |
|  **hatch-\<breeds\>** number \[ commands \] | Creates *number* new turtles with all the same values for its variables (including coordinates) except the *who* index |
|  **create-link-with** turtle number | Creates a link between this turtle and the turtle *number* |
|  **patch-at** xoffset yoffset | This reporter reports the first patch at an *xoffset* and *yoffset* distance from the turtle who asked |

### Patch

* A portion of the floor where turtles can go
* Can't move, but is "as alive" as a turtle
* Can create turtles
* *pxcor* and *pycor* are necessarily integers
* The patch at (0,0) is called the origin
* *pycor* increases as you go up on the screen

|  Procedure/Variable | Description |
|  --------- | ----------- |
|  **sprout-\<breeds\>** number \[ commands \] | Creates *number* new turtles at this patch and then runs the *commands* on them|

### Link

* Agent that connects 2 turtles
* Has 2 ends which are the 2 turtles it connects
* If one of the turtles dies, the link dies too
* Doesn't have coordinates

### Observer

* Is not situated in the world
* Gives instructions to the other agents
* Can create turtles

## Procedures

They tell agents what to do. **Primitives** are built into Netlogo whilst **procedures** are the one we define ourselves. Their definitions always end with the **end** keyword.

### Command

* An action for an agent to carry-out, resulting in some effect
* Typically begins with a verb such as "create", "die", "jump", etc...
* We define them using the **to** keyword


### Reporters

* Instruction for computing a value, which the agent then "reports" to whoever asked it
* Its name typically is a noun or a noun phrase
* We define them using the **to-report** keyword

### Anonymous procedures

* Look like \[ var -> \[ commands \]\] and are often used with lists

## Agentsets

Exemple code to report agentsets :
```
other turtles ;; all other turtles
other turtles-here ;; on this patch
turtles with [color = red]
turtles-here with [color = red]
turtles in-radius 3
;; turtles in the first quadrant that are on a green patch
turtles with [(xcor > 0) and (ycor > 0)
              and (pcolor = green)]
;; turtles standing on my neighboring four patches
turtles-on neighbors4

patches with [pxcor > 0]
patches at-points [[1 0] [0 1] [-1 0] [0 -1]]
neighbors4 ;; shorthand for those four patches

;; all the links connected to turtle 0
[my-links] of turtle 0
```
We can then call one of those 4 procedures on agents :
  * **ask** to make them do something
  * **any?** to see if the agentset is empty
  * **all?** to see if they all satisfy a condition
  * **count** to report the size of the agentset <br/>

Or we can do more complex stuff :

  * ask **one-of** turtles \[ commands \] to randomly pick 1 agent
  * ask **max-one-of** patches \[ count turtles-here \] \[ commands \] pick the agent with the highest value for given reporter
  * **member?** agent agentset to report wether or not *agent* is in *agentset*
  * **turtle-set turtles** (respectively patches and links) to create a special independent agentset

##  Breeds

* Are either turtle breeds or link breeds

|  Procedure/Variable | Description |
|  --------- | ----------- |
|  **create-\<breeds\>** number \[ commands \] | Creates *number* new turtles at the origin with random parameters and then runs the *commands* on them |
|  **hatch-\<breeds\>** number \[ commands \] | The turtle who calls this method creates *number* new turtles which inherits all of its variables and then runs the *commands* on them |
|  **sprout-\<breeds\>** number \[ commands \] | The patch who calls this method creates *number* new turtles on it with random parameters and then runs the *commands* on them |
|  **\<breeds\>-here** \[ commands \] | Reports an agentset with all \<*breeds*\> turtles on the same patch |
|  **\<breeds\>-at** dx dy \[ commands \] | Reports an agentset with all \<*breeds*\> turtles at the patch at dx dy distance from here |
|  **\<breeds\>-on** agent (or agentset) \[ commands \] | Reports an agentset with all \<*breeds*\> turtles on the same patch that the give agent or agentset |
|  **is-\<breed\>?** value \[ commands \] | Reports true if value is a \<*breed*\> turtle |

## Lists

* Is ordered starting from 0
* Can contain any types all at the same time

|  Procedure/Variable | Description |
|  --------- | ----------- |
| **set** mylist \[ elem1 elem2 elem3 \] | Creates a list of constants describing its content |
| (**list** reporter-1 reporter-2 reproter-3) \] | Reports a list using reporters |
| **foreach** list \[ x -> \[ commands \] \] | Applies *commands* to each element of *list* which will be referenced as *x* in the commands |
| **map** \[ x -> \[ commands \] \] list | Reports a copy of *list* with *commands* applied to each of its elements referenced as *x* in the commands |
| **n-values** n \[ i -> \[ commands \] \] | Reports a list of n values and applies *commands* to each element index (starting 0) which will be referenced as *i* in the commands |
| (**sentence** \[1 2\] 3 \[4 5\] (3 + 3) 7) | Reports a list containing all values \[1 2 3 4 5 6 7\] |
| **replace-item** i mylist x | Reports mylist with element at index *i* replaced by *x* (*mylist* is not modified however) |
| **lput**(respectively **fput**) x mylist | Reports mylist with *x* added at the end (respectively at the beginning) |


## Shortcuts

| Shortcut | Description |
|  --------- | ----------- |
| *ctrl* **+** *-* | Hide the current procedure |
| *ctrl* **+** *+* | Show the current procedure |
| *ctrl* **+** *=* | Zoom in |
| *ctrl* **+** *-* ('6' dash) | Zoom out |
| *ctrl* **+** *;* |  Comment selection |


## Behavior Search

1. Design a quantitative measure for the behavior you're interested in.
2. Choose parameters to vary and what ranges are allowed.
3. Choose a search algorithm and run it.
4. Examine the results (what parameters most affect this behavior?)

## HubNet

HubNet adds a new dimension to NetLogo by letting simulations run not just according to rules, but by direct human participation.


