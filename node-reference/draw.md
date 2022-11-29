---
title: draw.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---

{%hackmd theme-dark %}

[User Guide Contents](https://hackmd.io/@k--5gSDXTFSeySUer_0emQ/BJEudBf-F)

### Draw


With the draw tool you can create vector based drawings as well as animate them.

#### Advantages of Mewa animations

Animations done with web technologies like CSS and SVG use a lot of CPU. Mewa animations run entirely on GPU. In pratical terms it means that web pages running mewa animations can load faster, run smoother animations, and be more responsive. All because a lot of the work done in the webpage is offloaded from CPU to GPU.


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

### Creating a shape

![](https://i.imgur.com/Gist6YO.png)

On the right side we have all the points that make the shape. Each point with its X and Y values in separate boxes.
Each box is a parameter.

To animate the geometry we se curves to the parameters we want to change over time.

Everytime I change the value of a parameter with a curve set it changes the curve.




### Export to HTML

Generates an html webpage that plays the created animation.

#### Javascript API

To interact with animations Mewa offers a javascript API.

Public API functions start with underscore.

In the example below the *setValue()* function sets a constant value to a parameter. Note that the *setValue()* function starts with an underscore.
```
<script type='text/javascript'>

    // Parameters list
    const Parameters = {
        const BubbleLayer = {
            BubbleX: 0,
            BubbleY: 1
        }
    }

    function onMouseClick()
    {
        // set value to parameter, constant through time
        _setValue( Parameters.BubbleLayer.BubbleX , 0.5 );
        _setValue( Parameters.BubbleLayer.BubbleY , 0.5 );
    }
    canv.addEventListener('click', onMouseClick, false);
    
</script>
```

### Custom Effects

Custom shaders can be added to *Draw* animation.

Input variables supported in Draw shaders are:

* iTime
* iResolution

### Related Resources

* [Script to draw custom shape](http://mewa.app/webstore/index.php?view=Rounded_Corners_Triangle)

