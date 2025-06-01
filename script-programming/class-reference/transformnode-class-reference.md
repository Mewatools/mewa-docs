---
title: transformnode-class-reference.md
tags: mewa-programming-reference
description: Mewa Programming Reference
---


## 📘 TransformNode — Class Reference

### 🛠️ Creation

```javascript
transform = nodegraph().addNode("Transform");
```

---

### 📍 Example: Center an Image

```javascript
transform = nodegraph().addNode("Transform");
transform
  .setPivot(0.5, 0.5) // center of the input image
  .moveTo(0.5, 0.5);  // center of the output frame
```

---

### 🔄 Example: Center, Rotate, and Scale an Image

```javascript
transform = nodegraph().addNode("Transform");
transform
  .setPivot(0.5, 0.5)    // rotate/scale around image center
  .moveTo(0.5, 0.5)      // place image in center of output
  .setRotation(45)       // rotate 45 degrees clockwise
  .setScale(1.5, 1.5);   // scale up by 1.5x
```

---

### 📚 Methods

| Method                  | Description                              | Units          |
| ----------------------- | ---------------------------------------- | -------------- |
| `moveTo(x, y)`          | Layout-style center positioning          | Normalized     |
| `setTranslation(x, y)`  | Pixel-perfect offset from current origin | Pixels         |
| `setPivot(x, y, unit?)` | Defines rotation/scale origin            | `norm` or `px` |
| `setRotation(degrees)`  | Rotates the input around the pivot       | Degrees        |
| `setScale(x, y)`        | Scales the input from the pivot point    | Multiplier     |

---

### 🔎 Coordinate Space Explanation

* The **pivot** is relative to the **input image**, not the output frame.
* It defines the point around which **rotation** and **scaling** are applied.
* By default, `setPivot()` uses **normalized** coordinates:

```javascript
transform.setPivot(0.5, 0.5); // center of the input image
```

* The `moveTo()` function repositions the **pivot point** in the **output frame**, using normalized coordinates.

---

### 📐 Coordinate Reference Table

| Operation                 | Coordinates      | Relative To            |
| ------------------------- | ---------------- | ---------------------- |
| `setTranslation(x, y)`    | Pixels           | Output frame           |
| `moveTo(x, y)`            | Normalized (0–1) | Output frame           |
| `setPivot(x, y, unit?)`   | Normalized or px | Input image            |
| `setRotation`, `setScale` | —                | Applied from the pivot |

---
