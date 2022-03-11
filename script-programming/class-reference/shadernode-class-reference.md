---
title: shadernode-class-reference.md
tags: mewa-programming-reference
description: Mewa Programming Reference
---


## ShaderNode class reference

### Constructors
#### ShaderNode( glslCode, nameHint )
#### ShaderNode( glslCode, name, pos )

Creates a ShaderNode, with the given *glslCode*, and adds it to the node-graph.

*nameHint* is the name given to the node while generating a unique name for the node. 
If there is already a node with name *nameHint* a number will be added at the end of the *nameHint* to make it unique.

If *pos* is not provided the node will be placed at a "best guess" position.

The best way to learn on how to create shader nodes is to look at examples.
Mewa web store provides many scripts with it's source available. One example is [Ether](https://mewatools.com/webstore/index.php?view=Ether)

To fill the node's panel use the functions [*addFloatControl*](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#addFloatControl-variableName--defaultValue-), [*addVec2Control*](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#addVec2Control) and [*addColorControl*](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#addColorControl-variableName-).
Each of those functions adds one row to the node's panel, starting from the bottom.

### Controls

Controls are graphical widgets used to change the value of input variables in the shader program. There are 3 different control types:
* *addFloatControl* connects to a input variable of type *float*
* *addVec2Control* connects to a input variable of type *vec2* 
* *addColorControl* connects to a input variable of type *vec3*

By default the controls will show the name of the variable as a text label. The label text can be modified by through the function:
* setName( name )

The control name should be unique within the node as the *name* can be used in the control search.

#### addFloatControl( variableName , defaultValue )
Adds a GUI control to the node [parameters window](https://hackmd.io/VIsuWHCySFWk6j2shR36zw?view#Parameters-window). The GUI control changes the value
of a variable in the shader program. The variable is of *float* data type.

*variableName* is the name of variable in the shader source that will be controlled.

![](https://i.imgur.com/FRnroxw.png)*Float control*

Returns a [FloatControl](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#FloatControl) object.

#### addVec2Control( variableName, defaultValues )

![](https://i.imgur.com/bF81GSl.png)*Vec2 Control*

Returns a [Vec2Control](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#Vec2Control) object.


#### addColorControl( variableName )
This function creates a [ColorControl](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#ColorControl) connected to variable with name ''variableName'' and initialized with black color (0,0,0).
See more at [ColorControl](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#ColorControl).

#### addColorControl( variableName, gray )
''gray'' argument is a number.
This function creates a [ColorControl](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#ColorControl) connected to variable with name ''variableName'' and initialized with ''gray'' value set on the three channels R,G and B.

#### addColorControl( variableName, red, green, blue )



The color control has 3 parameters. Clicking on the color button expands to show the 3 parameters.

### addShaderInput( input )
Adds an input to *mainImage* function inside the GLSL code.
The *input* must be ***iResolution***, ***"iChannel0"*** or ***"iChannel1"***. 


* An example of a node using **addShaderInput("iResolution")** is [Ether](https://mewatools.com/webstore/index.php?view=Ether). This example uses the input coordinates passed into *fragCoord* in 
```javascript
mainImage( out vec4 fragColor, in vec2 fragCoord )
```
to generate a procedural image. Because "iResolution" option fills the entire viewport using ''fragCoord'' with values that go always from 0 to 1, this option is mostly used to generate images.
* An example of a node using **addShaderInput("iChannel0")** is [HexPixelate](https://mewatools.com/webstore/index.php?view=HexPixelate). The *iChannel0* option automatically adds an input port to the node. to connect an input image. The input coordinates ''fragCoord'' passed into 
```javascript
mainImage( out vec4 fragColor, in vec2 fragCoord )
```
cover only the input image. Also, note that ''fragCoord'' coordinates can have any range of values within the 0 to 1 limits. Use the texture size in variable ''iChannelResolution[0]'' to get, always, a 0 to 1 range in the ''fragCoord'' input variable. The ''iChannel0'' option is aminly aimed at the creation of image processing nodes, taking an input image for processing and outputing the result. 
* An example using **addShaderInput("iChannel0")** and **setInputMapping("iChannel1")** can be found in [OverlayBlend](https://mewatools.com/webstore/index.php?view=OverlayBlend). This option is mostly used to merge 2 images. It adds 2 input ports to the node. When using the ''iChannel0+iChannel1'' option make sure to be use 
```javascript
mainImage( out vec4 fragColor, in vec2 fragCoordA, in vec2 fragCoordB )
```
function in your shader source to access the texture coordinates of both images. Use the texture size in variable ''iChannelResolution[0]'' to get, always, a 0 to 1 range in the ''fragCoord'' input variable.


### setFilter( channel, filter )
Options are Nearest, Linear or Mipmap
### setWrap( channel, filter )
Options are Clamp or Repeat.

### setFlip( channel, filter )
Options are NoFlip, HorizontalFlip or VerticalFlip.
