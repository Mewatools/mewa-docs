---
title: expressions.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---


## Expressions in Parameters

One of the more powerful aspects of Mewa is its ability to use a wide variety of expressions and script code directly
into any parameter.

### Editing a parameter expression

Parameter expressions are set in the expression box that becomes visible when clicking on 
![](https://upload.wikimedia.org/wikipedia/commons/d/d7/NodeLibraryButton.png) button.

![](https://www.mewatools.com/downloads/logo/mewa-128x128.png)*Expression editing box*

The expression box button is gray if no expression is set and yellow if there is an expression associated with it.

![](https://www.mewatools.com/downloads/logo/mewa-128x128.png)*Parameter with expression and without expression*


### Curves in Parameters

Curves are the most used method to animate parameters, and so, it's usefull to know

By default a prameter shows 2 buttons, the *new curve* button ![](https://upload.wikimedia.org/wikipedia/commons/8/82/NewCurveButton.png)
and the *expression* button ![](https://upload.wikimedia.org/wikipedia/commons/8/82/NewCurveButton.png)

![](https://i.imgur.com/5Ogmeaf.png)*Node and it's Parameter window*


When a curve is set to a parameter it shows two arrow buttons.

![](https://i.imgur.com/qBKSy4g.png)*Node parameter with curve associated*

The arrow buttons are in the color of the curve and they move the play-head to the previous or next curve point.

Parameters using curves are in practice using an expression. Opening the expression box we should see a similar expression to:

```javascript
curve("myCurve").value( frame() )
```
A breakdown understanding of the expression:
* The [*curve()*]() function finds a curve with the given name
* The [*value()*]() method returns the curve (*y* value) for the given input *x*
* The function [*frame()*]() returns the current position of the playhead.

Value at a Different Frame

If a parameter is animated and you want to obtain a value at a specific frame, or at a frame that’s offset from the current time.

For example, the following expression obtains the value from ''Move2D@x'' curve at the previous frame:

```javascript
curve("Move2D@x").value( frame() - 1 )
```

### Linking Parameters


"linked parameter" is the term used to describe a node parameter which value is shared with other node parameters.

To refer to the value of a parameter we create an expression that finds the node parameter and returns it's value.

```javascript
node("Move2D").value("Translation", 0)
```

The Move2D node has a parameter called translation which returns an array with size 2. Because we want the x value we pass 0 as index value. 

```javascript
t = node("Move2D").value("Translation");
return t(0);
```







