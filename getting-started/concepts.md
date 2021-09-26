---
title: concepts.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---

## Concepts - a sketch approach

Video compositing is the technique used in post-production and video games to create visual effects. It requires expensive software, and the learning curve can be very steep due to its complexity. 

The purpose of this article is to explain the basics of node-graph based compositing through sketch images.

### The node-graph
 
Consider the node-graph below. It has 3 nodes connected with edges. The Nodes represent operations and images are the data flowing through the edges, from top to bottom. In the node-graph below the **Video** node outputs a video frame, which is then pixelated by the **Pixelate** node and finally translated by the **Move2D** node. 

![](https://i.imgur.com/838XdoT.png) 
[(edit drawing)](https://docs.google.com/drawings/d/1nfwEwlny_lfZkSZOF0sv8RfEMEksfQpeqjE1rgJKP8o/edit?usp=sharing)

Through the node-graph interface, we can choose which node output we want to inspect.

The output of the **Video** node 

![](https://i.imgur.com/4bwLJMe.png)
[(edit drawing)](https://docs.google.com/drawings/d/1mRpwuXL9-dPcTIFP4-yzQLwq8hvkLCgX70YT5QjgyOY/edit?usp=sharing)



The output of the **Pixelate** node


![](https://i.imgur.com/gYfF2Sx.png)
[(edit drawing)](https://docs.google.com/drawings/d/1HnjZZPKGB9xCqoL1LvH3IRrt8ep9VDWPl-HjD1z0Y0s/edit?usp=sharing)

Output of **Move2D** node. (Note that the video image is moved)

![](https://i.imgur.com/TJjQTIr.png)
[(edit drawing)](https://docs.google.com/drawings/d/170VGjPunfKmIUiacrpMpqFKl_1la1Z94TIGHGUHorRk/edit?usp=sharing)

Nodes also have parameters, shown in the parameters window.
Through the parameters window, we can change the pixelation parameter while watching the output at the **Move2D** node.


![](https://i.imgur.com/5RXIOcu.png)
[(edit drawing)](https://docs.google.com/drawings/d/1GxROhz2fKURvcPfI20-5O19WvVUdidvmOeICUQkDsO4/edit?usp=sharing)



With a node-graph interface, we can watch the output of a selected node while modifying any parameter.

### Animating parameters


Below we have the **Move2D** node with it's parameters window open showing the scale parameters.

![](https://upload.wikimedia.org/wikipedia/commons/b/b9/TimelineSketch1.png)
[(edit drawing)](https://docs.google.com/drawings/d/1TwOP7ggREIRYRzJ_9Mrz9M9i_UG4SC4bGS2E6g6fpDc/edit?usp=sharing)

![](https://upload.wikimedia.org/wikipedia/commons/b/b8/TimelineSketch2.png)
[(edit drawing)](https://docs.google.com/drawings/d/1gTIw44MYDMDtkHEkIedSsYzVlqAd4i9D8RvG67hCotY/edit?usp=sharing)

To produce animations we set different parameter values at different frames/time.

The most common way to animate a parameter is by associating a curve to a parameter.

![](https://upload.wikimedia.org/wikipedia/commons/3/34/TimelineSketch3.png)
[(edit drawing)](https://docs.google.com/drawings/d/10F0M6fCBUei9wTIMYcsY10U6LwX0ua2huyJc0s85pss/edit?usp=sharing)

