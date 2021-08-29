---
title: custom-shaders.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---


## Extending Mewa with custom shaders

This chapter explains how to extend Mewa with custom GLSL shaders. 

The GLSL shader code is held by a node, the [ShaderNode]().

At the core of Mewa is a script engine that executes Mewa script files. Mewa scripts are text files with ''.mw'' file extension.
Nodes are created through the execution of a script.

The available scripts are listed in the [Main window#Nodes menu](). 
The names shown in the menu are the scripts' file name.
Clicking in a menu entry will execute the respective script.

![](https://upload.wikimedia.org/wikipedia/commons/0/0b/NodeListMenu.png)*List of scripts*


### Modify existing nodes

When creating Mewa nodes it is a good idea to look at examples and modify them. Mewa script files are located in the [[Mewa User's Guide/Extending Mewa with custom shaders#The Scripts directory|scripts directory]].
Open any script file, apply some changes and execute it to observe the result.

If there’s a particular node that you would like to modify or customize for a specific use, you 
can check it's source by saving your current work into a (project) script. 

The GLSL shader code of all Shader nodes are explicitly stored in the project scripts.

All nodes are created from a script, except that you create your own custom node using
Mewa's other nodes as the initial shader program.

You can then add your own expressions, scripting, and user
interface elements to extend their functionality.


### A simple example

Let's start with a simple script.

In this example, we will create a script that will generate a new node called ''MyImage''. 
To create the script make a new text file named ''MyImage.mw'' and paste the text below into the file.

<syntaxhighlight lang="JavaScript">
// this is a mewa script that creates a node with a custom shader
shaderSource = "
void mainImage( out vec4 fragColor, in vec2 fragCoord )
{  
    vec3 col = 0.5 + 0.5*cos( iTime + fragCoord.xyx + vec3(0,2,4) );
    fragColor = vec4(col,1.0);
}";

addShaderNode("MyImage", shaderSource);
</syntaxhighlight>

The Mewa script file above contains the GLSL shader code, within quotation marks, and a Mewa API call to create the Mewa node.

The shader code implements the mainImage() function. This function is called once per pixel. 
The ''fragCoord'' argument contains the pixel coordinate in normalized coordinates. ''fragCoord'' values range always from 0 to 1, and covers the whole viewport.
The output color for each pixel is stored in ''fragColor''.

The variable ''iTime'' is an [[Mewa User's Guide/Extending Mewa with custom shaders#Run the script|input variable]] provided by Mewa. 


Now let's install it and run it.

### The Scripts directory
[[Image:AboutDialogWindow.png|right|thumb|About dialog window]]
Mewa script files are located in one directory, which we call the ''scripts directory''. Its location depends on the platform Mewa is running on. 

To find the ''scripts directory'', on Mewa's main window click [[Image:AboutIcon.png]]. The general information window will open showing the ''scripts directory''.

### Run the script

To run our newly created script open the [[Mewa User's Guide/Main window#Nodes menu|nodes menu]] clicking the nodes button [[Image:NodeLibraryButton.png]].
A list of all the scripts located inside the
[[Mewa User's Guide/Extending Mewa with custom shaders#The Scripts directory|scripts directory]]
is shown.

[[Image:MyImageMenu.png|center|thumb|Select ''MyImage'' script]]

The names shown in the nodes menu are the scripts' file names. To start the execution of our script click in ''MyImage'' entry.
A node called ''MyImage0'' is added to the node-graph. Clicking on the output button, the squared button on the right side of the node, opens the output window showing the output of our node. See screenshot below.

[[Image:MyImageNodeAndOutput.png|center|thumb|700px|''MyImage'' node and its output]]

### Shader inputs

Below is the list of all input variables that Mewa makes available to all shaders:

| Type | Name | Description |
|:---- |:---- |:----------- |
| vec3 | iResolution | Viewport resolution in pixels. z is aspect ratio (width/height) |
| float | iTime | Playback time in seconds |
| int | iFrame | Playback frame number |
| vec3 | iChannelResolution0, iChannelResolution1 | Input texture resolution for each channel. z is aspect ratio (width/height) |
| sampler2D | iChannel0, iChannel1 | Input channel |
| vec4 | iChannelRect0, iChannelRect1 | Channel rectangle in texture coordinates. Rectangle given as vec4( left, right, bottom, top ) |



### Add node inputs

In the [example](Extending Mewa with custom shaders#Example) we've created above, the result node has no inputs.

To produce a shader node that takes an input image we introduce the variable ''iChannel0'' to our shader source.

Let's now create a new text file named ''MyFilter.mw'' with the following content:

```javascript
shaderSource = "
   void mainImage( out vec4 fragColor, in vec2 fragCoord )
   {
       vec3 col = texture2D(iChannel0, fragCoord).rgb;
       fragColor = vec4(col,1.0);
   }";

node = addShaderNode("MyFilter", shaderSource);
node.setRenderArea( "iChannel0" );
```

Place the *MyFilter.mw* file in scripts directory and run it from the nodes menu.

[[Image:MyFilterNode.png|center|thumb|''MyFilter'' node]]

*MyFilter* node now offers 1 input and 1 output.

The shader simply renders the input texture into its output.

### Add GUI Controls

Now that we have a node running a shader let's add an input variable to the shader and change its value using a GUI control.

The script below adds the input variable ''uNumber'' into the shader source and a ''uiControl'' to control the value of the ''uNumber'' variable.

```javascript
shaderSource = "
   void mainImage( out vec4 fragColor, in vec2 fragCoord )
   {
       vec3 col = texture2D(iChannel0, fragCoord).rgb;
       col.r = uNumber; // uNumber is a variable of type float
       fragColor = vec4(col,1.0);
   }";

myNode = newShaderNode("MyFilter", shaderSource);
myNode.setRenderArea( "iChannel0" );

// Slider control
uiControl = node.addFloatControl("uNumber", 0.5);
uiControl.setText("MyControl");
uiControl.setStep(0.01);
uiControl.setRange(0, 1);
```

The last 4 lines of the script set up the GUI control. 

[[Mewa User's Guide/Script Function Reference#addFloatControl|addFloatControl]] creates the GUI widget and adds it to the node parameters window. Its arguments are the variable name, used inside the shader source, and its 2nd argument is its initial value.

The GUI controls are visible in Mewa through the node parameters. To open the node parameters click on the circular button on the right side of the node.

[[Image:MyFilterParameters.png|center|frame|''MyFilter'' node parameters]]

Change the parameter value and watch the result in the output window.

### setInputMapping()

As we build the node-graph, translating/scaling images is a common operation and the ability to limit the shader processing area inside the image rectangle is important to prevent the whole viewport from being rendered.

Depending on the use case of a node, we have to choose 1 of 3 options:

*'''"iResolution"'''
** The main function ''mainImage( fragColor, fragCoord )'' accepts 2 input arguments, where fragCoord goes always from 0 to 1, and covers the whole viewport. 
**Used to generate procedural images by computing the color for each pixel.
* '''"iChannel0"'''
** In this option the shader processes only the area covered by the image ''iChannel0''. The main function ''mainImage( fragColor, fragCoord )'' takes 2 input arguments with ''fragCoord'' holding the texture coordinates of the input image. ''fragCoord'' range does not necessarily starts at 0 and ends at 1, but it will be in any range within the 0 and 1 limits.
** Used to apply an image processing filters on an image
* '''"iChannel0+iChannel1"'''
** The main function ''mainImage( fragColor, fragCoord0, fragCoord1 )'' accepts 3 input arguments, with ''fragCoord0'' and ''fragCoord1'' the texture coordinates of the 2 input images
** Used to blend/merge 2 input images



For an example on how to use the "iChannel0+iChannel1" option see ''OverlayBlend.mw'' script located in your
[[Mewa User's Guide/Extending Mewa with custom shaders#The Scripts directory|scripts directory]].


### Publish Your Script

Scripts can be published in [Mewa WebStore](http://www.mewatools.com/webstore/index.php), an online repository of Mewa Addons.



