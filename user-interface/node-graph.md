---
title: node-graph.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---

{%hackmd theme-dark %}

[User Guide Contents](https://hackmd.io/@k--5gSDXTFSeySUer_0emQ/BJEudBf-F)

## Understanding the Node-graph

The node graph provides a visual representation of a sequence of operations applied over images.

![](https://upload.wikimedia.org/wikipedia/commons/9/93/NodeGraphScreenshot.png)

The node graph is represented by nodes connected to each other by lines. In this node-based workflow each node in the graph performs a specific function.

Node inputs are on the top of the node. Node outputs are on the bottom of the node. The output port of one node is attached to the input port of the next node down in the node graph.

Connections between nodes can only be done between input and output.

Nodes apply image processing operations over the input image and return the processed image in their output port.

As you create a node graph you will need to edit nodes parameters and visualize the output of different nodes. Parameter windows allow you to edit node's parameters while using the output window to inspect the out put of a node.

![](https://i.imgur.com/5Ogmeaf.png)*Parameters window*

Inside the nodes there are 2 buttons. On the left side, with a rectangular shape is the *output button*. On the right side, with a circular shape is the *parameters button*.

![](https://www.mewatools.com/downloads/logo/mewa-128x128.png)*Node Buttons*

To bring up the parameters window just click on the node *parameters button*. A parameters window pops up showing the node's parameters. Some nodes, like move2D node, have parameters that will be shown on the output window.

The output window as a similar behaviour as the parameters window. To show the output window use the node's button located on the left side of the node. 


Using the parameters window to modify one node parameter while visualising the result at a different node is one of the great advantages of using a node graph.

![](https://www.mewatools.com/downloads/logo/mewa-128x128.png)*Working with images in the node-graph*






## Navigating the Node-graph

### Pan
The mouse middle button to pans the node graph view.
## Editing a Node-graph
### Adding new nodes
To add nodes to the node graph use the ![](https://upload.wikimedia.org/wikipedia/commons/d/d7/NodeLibraryButton.png) button to show the list of all available nodes. Just click the node you wish to add and the corresponding node will be added to the Node graph.

![](https://upload.wikimedia.org/wikipedia/commons/0/0b/NodeListMenu.png)*Node List*

Footage nodes are added to the node-graph when importing footage. See chapter [Import Footage](import-footage.md) for more information.

### Moving Nodes
To move a node, select the node and drag it within the node-graph window.

### Connecting Nodes
Connections between nodes are drawn as a cubic spline line between 2 nodes. To connect two nodes, with the left mouse button, click and drag from one node input/output releasing over another node output/input.

Note that only connections between inputs and outputs are allowed.

Node inputs/outputs provide information whether a connection is allowed or not. An input/output becomes highlighted when hovering the mouse pointer over it, meaning 
the connection can be created to the dragging edge. If a connection is not allowed, the destination input/output does not get highlighted.

### Disconnecting nodes
To disconnect nodes, drag one end of the connection and drop it away from the node.

## Parameters window

![](https://i.imgur.com/5Ogmeaf.png)*Node and it's Parameter window*

An animation is created by changing the value of a parameter over time. A parameter can be anything from the position, rotation, scaling, or transparency of an object, to the gamma, gain, or offset in a color correction. Basically, any node parameter can be animated.

Parameters of a node are listed in the node's parameter window.
To open the parameters window toggle the *parameters button* found inside the node, on the right side. 

For some nodes enabling the node parameters not only opens the parameters window, it can also show an extra toolbar in the output window. An example of this is the move2D node.

![](https://upload.wikimedia.org/wikipedia/commons/0/0b/Move2DOutputWithParameters.png)


### Changing a parameter value
Parameters are made up of an input box that shows the parameter value.

![](https://i.imgur.com/FRnroxw.png)*Node Parameter*

To change the value of a parameter press-down inside the input box, and move the cursor as if dragging. Dragging to the left decreases the parameter value, while dragging to the right increases the parameter value.

An overlay with multiples of 10 is shown while changing the parameter value. That's the 'step' value, the increment amount added to the parameter value for each cursor movement.

![](https://upload.wikimedia.org/wikipedia/commons/f/f2/ParameterStepSelection.png)*Selecting step*

The current 'step' value is not shown in the overlay, instead only 'step' values above and below the current 'step' value are shown. To select a different 'step' value move the cursor over it.

### Controlling a parameter with a curve

Parameters are animated using curves. The curve represents the value of a parameter at different frames.

A curve can be created in two ways:
*clicking on *new curve* button ![](https://upload.wikimedia.org/wikipedia/commons/8/82/NewCurveButton.png) in the curve editor,
*or pressing the ''curve button'' in the parameter input box (see image below)

More information on how to create a new curve using the *new curve* button ![](https://upload.wikimedia.org/wikipedia/commons/8/82/NewCurveButton.png) can be found in [curve editor](curve-editor.md).

Creating a curve from the parameter input box is my favorite method because it has the advantage of creating a new curve and associating it with the parameter at the same time.

Any curve can be associated to a parameter and the same curve can be associated to as many parameters as desired.

When a parameter has a curve associated with it two buttons are shown in the parameter input box. Below is a pic of a parameter control with a curve associated with it.

![](https://i.imgur.com/qBKSy4g.png)*Node parameter with curve associated*


The parameter input box has two buttons, the first button is a single color button. The color is the color of the curve as seen in the curve editor. Clicking on it will show a drop down list of all available curves. This allows to choose a different curve to be associated with the parameter.

The first button ![](https://i.imgur.com/YGqDkeW.png) detaches the curve from the parameter. This means the parameter will have the same value in all frames.

## Output window
The output window is where the output of a node is shown.

Below is a node with it's output button toggled. On the left is the output window showing the node output.

![](https://upload.wikimedia.org/wikipedia/commons/4/45/NodeOutputWindow.png)*Output of a image node*


Note that the output window header, at the top of the window, shows the name of the node owning the output window.

Usually node parameters are changed while watching the result at the output window. This ability to choose to view the output of any node while changing parameters from a different node is one of the main benefits of working with a node graph.


### Fit in view

The *Fit in view* button ![](https://upload.wikimedia.org/wikipedia/commons/9/9f/FitInViewButton.png) scales the output image to be fully visible in the output window.
