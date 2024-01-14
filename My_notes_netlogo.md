# Netlogo : notes

## Agents

### Turtles

* Have positions in the World
* *xcor* and *ycor* are not necessarily integers, turtles can be anywhere in a patch

|  Procedure | Description |
|  --------- | ----------- |
|  **hatch-<breed>** number \[ context \] | Creates *number* new turtles with all same values for its variables (including coordinates) except the *who* index |
|  Procedure | Description |

### Patch

* A portion of the floor where turtles can go
* Can't move, but is "as alive" as a turtle
* Can create turtles
* *pxcor* and *pycor* are necessarily integers
* The patch at (0,0) is called the origin
* *pycor* increases as you go up on the screen

### Link

* Agent that connects 2 turtles
* Has 2 ends which are the 2 turtles it connects
* If one of the turtles dies, the link dies too
* Doesn't have coordinates

### Observer

* Is not situated in the world
* Gives instructions to the other agents
* Can create turtles

### World

* Is divided in a grid of patches

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

## Behavior Search

1. Design a quantitative measure for the behavior you're interested in.
2. Choose parameters to vary and what ranges are allowed.
3. Choose a search algorithm and run it.
4. Examine the results (what parameters most affect this behavior?)

## HubNet

HubNet adds a new dimension to NetLogo by letting simulations run not just according to rules, but by direct human participation.


