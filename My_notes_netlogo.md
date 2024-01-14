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


## Behavior Search

1. Design a quantitative measure for the behavior you're interested in.
2. Choose parameters to vary and what ranges are allowed.
3. Choose a search algorithm and run it.
4. Examine the results (what parameters most affect this behavior?)

## HubNet

HubNet adds a new dimension to NetLogo by letting simulations run not just according to rules, but by direct human participation.


