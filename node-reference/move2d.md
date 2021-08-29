---
title: move2d.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---

{%hackmd theme-dark %}

[User Guide Contents](https://hackmd.io/@k--5gSDXTFSeySUer_0emQ/BJEudBf-F)

### Move2D

The Move2D node is used for simple 2D transformations, such as moving and scaling. 
The image’s aspect can also be modified using the scale parameters.

#### Parameters


| ***Parameter*** | Description |
|:--------------- |:----------- |
| Translation | x and y trnaslation relative to the bottom-left corner |
| Scale | is applied to the width and height of the input image |

There are 2 types of controls to adjust the image position and scale:
Edge controls: Follow the edge of the image. Moving or scaling the image is performed by grabbing the edge or corner of the image.
Grid controls: Is a 3x3 grid that stays fixed at the center of the view. Dragging a cell of the grid moves the correspondent corner/edge of the image. It’s useful to adjust parameters when using a high zoom level.


