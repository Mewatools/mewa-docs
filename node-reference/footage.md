---
title: footage.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---

{%hackmd theme-dark %}

[User Guide Contents](https://hackmd.io/@k--5gSDXTFSeySUer_0emQ/BJEudBf-F)

### Footage Node



Footage node holds a sequence of images. Images are indexed from 0 to N, N being the number of images/frames.

Footage nodes are added to the node-graph from the [[Mewa User's Guide/Import footage|file browser]]. 
To open the file browser click ![](https://upload.wikimedia.org/wikipedia/commons/7/77/OpenButton.png).

Imported footage from the [Mewa User's Guide/Import footage#file browser]() appears in the node-graph as a new node.
The node has the name of the imported file.

![](https://i.imgur.com/hvs0FsM.png)
*Footage node*



A status bar message is displayed while hovering the mouse cursor over a footage node. This status bar message shows the footage resolution, number of frames
and the footage file name.

#### Parameters

![](https://i.imgur.com/sJMs36m.png)*Footage parameters*


##### Frame Index===

The footage node holds a sequence of images, indexed from 0 to N.
By default, when a footage node is created a new curve is created mapping the image index to the frame number, as shown

![](https://upload.wikimedia.org/wikipedia/commons/d/d9/DefaultFrameIndexCurve.png)*Default frame index curve*

The default frame-index curve is a diagonal curve that goes from 0 to N, N being the number of images in the footage node.

To holding a frame we repeat a given image index for several time frames.

![](https://upload.wikimedia.org/wikipedia/commons/3/38/HoldFrameIndexCurve.png)*Frame index curve with holding frames*


Trimming erases images from the footage node.

![](https://upload.wikimedia.org/wikipedia/commons/7/73/TrimFrameIndexCurve.png)*Frame index curve trimming the first 2 frames*



