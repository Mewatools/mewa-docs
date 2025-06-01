---
title: transformnode-class-reference.md
tags: mewa-programming-reference
description: Mewa Programming Reference
---


## TransformNode class reference

### Creation
```javascript
transform = nodegraph().addNode("Transform");
```

#### Example : center image

```javascript
transform = nodegraph().addNode("Transform");
transform
  .setPivot(0.5, 0.5)
  .moveTo(0.5, 0.5)
```

#### Example : center, rotate and scale image

```javascript
transform = nodegraph().addNode("Transform");
transform
  .setPivot(0.5, 0.5)
  .moveTo(0.5, 0.5)
  .setRotation(45)
  .setScale(1.5, 1.5);
```


### Methods


| Method                 | Purpose                         | Units      |
| ---------------------- | ------------------------------- | ---------- |
| `moveTo(x, y)`         | Layout-based center positioning | normalized |
| `setTranslation(x, y)` | Pixel-perfect offset            | pixels     |
| `setPivot(x, y, unit)` | Defines rotation/scale origin   | norm or px |
| `setRotation(degrees)` | Rotate around pivot             | degrees    |
| `setScale(x, y)`       | Non-uniform scaling             | multiplier |


The pivot is relative to the input image. It determines the "origin" for operations like rotation and scale — both of which are internal to the element before it's positioned.

Also, the moveTo method applies the translation to the pivot.

```javascript
transform.setPivot(0.5, 0.5); // normalized to the input (the image)
```

| Operation                 | Coordinates      | Relative To            |
| ------------------------- | ---------------- | ---------------------- |
| `setTranslation`          | Pixels           | Output frame           |
| `moveTo`                  | Normalized (0–1) | Output frame           |
| `setPivot`          | Normalized (0–1) | Input image        |
| `setRotation`, `setScale` | —                | Applied from the pivot |


---
title: transformnode-class-reference.md
tags: mewa-programming-reference
description: Mewa Programming Reference
---


## TransformNode class reference

### Creation
```javascript
transform = nodegraph().addNode("Transform");
```

#### Example : center image

```javascript
transform = nodegraph().addNode("Transform");
transform
  .setPivot(0.5, 0.5)
  .moveTo(0.5, 0.5)
```

#### Example : center, rotate and scale image

```javascript
transform = nodegraph().addNode("Transform");
transform
  .setPivot(0.5, 0.5)
  .moveTo(0.5, 0.5)
  .setRotation(45)
  .setScale(1.5, 1.5);
```


### Methods


| Method                 | Purpose                         | Units      |
| ---------------------- | ------------------------------- | ---------- |
| `moveTo(x, y)`         | Layout-based center positioning | normalized |
| `setTranslation(x, y)` | Pixel-perfect offset            | pixels     |
| `setPivot(x, y, unit)` | Defines rotation/scale origin   | norm or px |
| `setRotation(degrees)` | Rotate around pivot             | degrees    |
| `setScale(x, y)`       | Non-uniform scaling             | multiplier |


The pivot is relative to the input image. It determines the "origin" for operations like rotation and scale — both of which are internal to the element before it's positioned.

Also, the moveTo method applies the translation to the pivot.

```javascript
transform.setPivot(0.5, 0.5); // normalized to the input (the image)
```

| Operation                 | Coordinates      | Relative To            |
| ------------------------- | ---------------- | ---------------------- |
| `setTranslation`          | Pixels           | Output frame           |
| `moveTo`                  | Normalized (0–1) | Output frame           |
| `setPivot`          | Normalized (0–1) | Input image        |
| `setRotation`, `setScale` | —                | Applied from the pivot |


