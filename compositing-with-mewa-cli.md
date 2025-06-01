---
title: compositing-with-mewa-cli.md
tags: mewa-programming-reference
description: Compositing with Mewa CLI
---



# 🎞️ Compositing with Mewa CLI

**Mewa CLI** is a console application that executes **Mewa scripts** for video compositing. It can render nodegraph-based compositions either **on-screen for preview** or **off-screen as image sequences**.

---

## 📦 Features

* Execute Mewa scripts from the command line.
* Render frames to the screen (interactive) or off-screen (batch export).
* Output to image sequences for integration with other tools or pipelines.

---

## 🧪 Usage

```bash
mewa-cli [options]
```

### Options

| Flag          | Description                                               |
| ------------- | --------------------------------------------------------- |
| `-i <script>` | Specify the input **Mewa script** file                    |
| `-f <range>`  | Specify the **frame range** to render (e.g., `0:100`)     |
| `-o <dir>`    | Specify the **output directory** for off-screen rendering |

---

### 📝 Example 1: On-Screen Preview

```bash
mewa-cli -i my_composition.mewa
```

This will execute the script and preview the nodegraph on-screen.

---

### 📝 Example 2: Off-Screen Render

```bash
mewa-cli -i my_composition.mewa -f 0:100 -o ./output/frames/
```

This renders frames `0` through `100` and saves them as an image sequence inside the `./output/frames/` directory.

---

## 🧠 Notes

* **Script files** must define a valid Mewa compositing nodegraph.
* When rendering off-screen, each frame is exported as a separate image (e.g., `frame_0000.png`, `frame_0001.png`, etc.).
* Output directories must be writable; they will not be created automatically if they don't exist.

---

## 📂 Sample Folder Structure

```
project/
├── my_composition.mewa
├── assets/
│   └── pic1.png
└── output/
    └── frames/
        ├── frame_0000.png
        ├── frame_0001.png
        └── ...
```

---

## 🚀 Future Plans

* Support for rendering to video formats (e.g., `.mp4`, `.mov`)
* Logging and performance metrics
* Integration with `mewa.app` desktop and web UI

---

