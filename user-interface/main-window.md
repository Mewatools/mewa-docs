---
title: main-window.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---

## Main Window

Below is Mewa's main window when we launch it for the first time.

At the top is the app bar with 3 buttons. Just below is a big empty area, that's the node-graph window, because it has no nodes it looks empty. 
Below is node-graph window is the timeline that contains play buttons and a play bar. At the bottom end is the status bar used to show usefull tips and information.

[Main window initial state](https://upload.wikimedia.org/wikipedia/commons/8/88/MainWindowEmpty.png)*Main window initial state*


### Main Toolbar

The app bar is at the top of the application window and offers the following options:


| Button | Description |
|:------ |:----------- |
| ![](https://upload.wikimedia.org/wikipedia/commons/7/77/OpenButton.png)*Import footage* | Show/hide file browser window. More about footage window at chapter [Import footage]() |
| ![](https://upload.wikimedia.org/wikipedia/commons/d/d7/NodeLibraryButton.png)*Node library* | Shows a list of available nodes |
|  New | Clears work. Used to start a new project |
|  Save | Saves current work state into a (project) script |
| ![](https://upload.wikimedia.org/wikipedia/commons/4/42/StoreIcon.png)*Store* | Show/hide store window |
| ![](https://upload.wikimedia.org/wikipedia/commons/c/c1/AboutIcon.png)*General info* | Show/hide window holding app version and Scripts folder path |

The *Save* button saves the current work state (or project) into a script (*.mw* file).
Running the project script restores the work state.
Saving projects as Mewa scripts allows users to turn a project script into a custom tool, as you can modify your own
project script to procedurally perform what would
otherwise be tedious operations.
You can also quickly make minor modifications to the script to perform operations that
would be repetitive or time consuming to do using the Mewa graphical interface.


### Nodes menu
The nodes button shows a list of all available nodes.

![](https://upload.wikimedia.org/wikipedia/commons/0/0b/NodeListMenu.png)*Nodes button*


When a node is selected from this list the correspondent node is added to the node graph.

For those who know GLSL programming, check out how to create custom nodes using a GLSL shader at [Extending Mewa with custom shaders]().

### Status bar

The status bar is the short horizontal bar located at the end bottom of the application window.

The status bar is feedback area that provides quick tips and other helpful information.
As the mouse pointer moves over an user-interface element (e.g. button) information related to the user-interface element is shown in the status bar.

Examples:
* Moving the mouse over a button the status bar shows a tip of what the button does,
* Moving the mouse over the help button, in parameters window, the status bar shows the web page link it will open,
* Moving the mouse over a node the status bar shows brief information about the node
* Moving a point in the [curve editor]() the status bar shows the new point time/value

### Time-view

While the [node graph](https://hackmd.io/@k--5gSDXTFSeySUer_0emQ/SkGOcUEbY) provides a visualization of the different operations in the workflow, this workflow changes through time.
The time-view provides the controls to navigate through time.

![](https://upload.wikimedia.org/wikipedia/commons/3/3d/MewaTimeline.png)*Time-view*

The playbar shows a time scale and a red vertical line, pointing to the current frame number, which we call play-head.
Both the image shown in the output window and the values shown in the node parameters window, are all respective to the selected frame, pointed by the play-head.


**Player buttons**

The player toolbar allows you to navigate trough frames, changing the current frame number.

The input box field in the player toolbar shows the current frame number.

The player buttons are explained in the table below,

| Button | Description |
|:------ |:----------- |
| ![](https://upload.wikimedia.org/wikipedia/commons/d/d2/ShowCurveEditorButton.png)*Expand time-view* | Expand time-view to show curve editor |
| ![](https://upload.wikimedia.org/wikipedia/commons/5/50/JumpStartIcon.png)*First frame* | Jump to frame 0 |
| ![](https://upload.wikimedia.org/wikipedia/commons/5/57/PreviousFrameIcon.png)*Previous frame* | Jump to previous frame |
|  Next frame | Jump to next frame |


The play-bar, located above the player toolbar, allows the quick navigation through frames. 
Clicking and dragging in the play-bar changes the current frame. A red vertical line, called the play head, shows where the current frame number is in the play-bar scale.

### Store Window

Mewa can be extended with nodes and other tools. These nodes and tools are available in Mewa Store.
To open the Mewa Store click ![](https://upload.wikimedia.org/wikipedia/commons/4/42/StoreIcon.png). 

Below is a screenshot of Mewa main window with the Store open. 

![](https://upload.wikimedia.org/wikipedia/commons/8/8d/StoreInMainWindow.png)*Store Window*

The store window lists its content in rows, with an image illustrating the node behavior on the left and a node description on the right.
To increase the store image size and description area you can resize the store window by dragging the splitter (located at the left edge of the store window).

Each node listed in the store window shows an install/uninstall button.
Click the install button to make the node available in the [Mewa User's Guide/Main window#Nodes menu|nodes menu]().

Nodes are created through the execution of a Mewa script which contains a program.
To create your own nodes with your developed program see [Mewa User's Guide/Extending Mewa with custom shaders]().

To publish a Mewa script in Mewa Store login to [Mewa Web Store](http://mewatools.com/tools/) and submit your script.


