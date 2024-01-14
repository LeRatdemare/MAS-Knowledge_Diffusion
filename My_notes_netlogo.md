# Netlogo : notes

## Agents

### Turtles

* Have positions in the World
* *xcor* and *ycor* are not necessarily integers, turtles can be anywhere in a patch

### Patch

* A portion of the floor where turtles can go
* Can't move, but is "as alive" as a turtle
* Can create turtles
* *pxcor* and *pycor* are necessarily integers
* The patch at (0,0) is called the origin
* *pycor* increase as you go up on the screen

### Link

* Agent that connects 2 turtles
* Has 2 ends which are the 2 turtles it connects
* If one of the turtles dies, the link dies too
* Doesn't have coordinates

### Observer

* Is not situated in the world
* Gives instructions to the other agents
* Can create turtles

## World

* Is divided in a grid of patches

## Behavior Search

1. Design a quantitative measure for the behavior you're interested in.
2. Choose parameters to vary and what ranges are allowed.
3. Choose a search algorithm and run it.
4. Examine the results (what parameters most affect this behavior?)

## HubNet

HubNet adds a new dimension to NetLogo by letting simulations run not just according to rules, but by direct human participation.


