---
title: curve-class-reference.md
tags: mewa-programming-reference
description: Mewa Programming Reference
---


## Curve class reference

Curves should be added to the curve editor only after they have been populated.

```javascript
curve1 = Curve( "MyCurve", [0.4, 0.3, 0.8], [0, 0] );
curve1.addPoint( [3, 0] );
curveEditor().addCurve(curve1);
```

Only after a curve is added to the curve editor the curve becomes visible in the curve editor.


### Contructors

* **Curve( *name*, *color*, *pos*, *leftCotrol*, *rightControl* )**

Example:
```javascript
Curve( "MyCurve", [0.4, 0.3, 0.8], [0, 0] );
```

The *name* argument is the name shown in the curve editor [curve list view](https://hackmd.io/0yBKMK5MR4aTHe4IfGDqAw#The-Curve-Editor-window).

The *color* argument is an array containing the RGB values in the 0 to 1 scale.

The argument *pos* is an array of size 2 containing the frame number and its value.

*leftCotrol* and *rightControl* are optional inputs, with the default value of [0,0]. They are the poisitions of the cubic bezier control points, whenever bezier interpolation is set. Their values are in the range of 0 and 0.5, which is the percentage relative to the previous/next point.

### Methods

#### addPoint( name, color, pos )

Example:
```javascript
curve1 = curveEditor().addCurve( "MyRedCurve", [1.0, 0.0, 0.0], [0, 0] );
// add point at frame 12
curve1.addPoint( [12, 0] );
```


