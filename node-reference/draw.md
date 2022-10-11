---
title: draw.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---

{%hackmd theme-dark %}

[User Guide Contents](https://hackmd.io/@k--5gSDXTFSeySUer_0emQ/BJEudBf-F)

### Draw


With the draw tool you can create vector based drawings as well as animate them.


![](https://i.imgur.com/Dk73byA.png)


Add draw objects and adust their positions on the output view.



#### Output View

The output of the draw is delimited by the red bounding box.

#### Output Toolbar

The Draw output toolbar contains the *New Object* button that shows a list of the different objects that can be added to the (canvas? draw-stack? scene?).

If something is selected the output toolbar will also show:
* Edit Vertices button
* Animate button ![](https://i.imgur.com/u3spLyO.png) : Sets animation curves to the selection vertices. This means that any position change in the selection will only affect the current frame.
* Set still button ![](https://i.imgur.com/LHmYzqT.png) : Removes all the curves associated to the selection, basicly making the selection have a fixed position througghout the animation.


#### Parameters Window

* **Object Tree-view** : List the objects being drawn
* **Selection View** : Shows the Parameters of the current selection. 
   * For shapes in edit mode the selection-view shows the positions of the selected vertices


The draw order of the objects is as listed by the tree-view, from top to bottom.



### Export to HTML

Generates an html webpage that plays the created animation.

### Custom Effects

Custom shaders can be added to *Draw* animation.

Input variables supported in Draw shaders are:

* iTime

### Related Resources

* [Script to draw custom shape](http://mewa.app/webstore/index.php?view=Rounded_Corners_Triangle)

