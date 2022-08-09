---
title: installing.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---
Installing Mewa
===

Although Mewa is currently only available for Linux and Windows, it aims to run across all platforms, including MacOS, tablet devices and chromebooks.

## On Linux


To install Mewa on Linux, open a command window and run the following command:

> sudo snap install mewa --edge --devmode

That's it, just type *mewa* on your command window to start the application.

#### Update an existing installation

If Mewa is already installed on your machine, type instead:

> sudo snap refresh mewa --devmode

## On Windows

There are 2 ways of installing Mewa on windows:
* Through the [Microsoft Store](https://www.microsoft.com/store/apps/9NRJM8F0MLN4)
* Through [Mewatools.com](https://mewatools.com/releases/windows/)


#### Troubleshooting
Mewa is an OpenGL application and in some windows machines the OpenGL driver needs to be updated.
If nothing is shown when you start Mewa application that's because you need to update the OpenGL drivers.

One way to update the OpenGL graphics driver is:

1. Open Device Manager
2. Expand Display adapters and then right click the graphics driver to Update driver
3. Try to Search automatically for the updated driver software

If the above method doesn't work the drivers needs to be updated manually:
1. Navigate to your graphics card manufacturer official website. (Intel, AMD or NVIDIA)
2. On the official site, navigate to the graphics driver and choose your operating system. Download the latest drivers for your graphics card and install it to your computer. This will also update the OpenGL on your computer.

## Web App

Alternatively you can run Mewa on the web browser, without the need to install anything. Just visit [mewa.club](https://mewa.app)

