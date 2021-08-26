---
title: function-reference.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---


### Functions

Below is the list functions supported in Mewa scripts.

Function names are shown as chapters to make the navigation easier thought the side menu.

If you need a function that is not currently available please [contact us](https://www.mewatools.com), we want to help you.


#### connectNodes( outNodeName, inNodeName, inputIndex )
Adds a connection between output of node with name *outNodeName* and input of node with name *inNodeName*.
*inputIndex* is the index of the input port.
Node input ports are indexed from 0 to N, where N is the number of input ports. In other words, the first input port of a node has index 0, the second input has index 1, and so on.

Example:
```javascript
connectNodes("ColorWheel", "OverlayBlend", 0);
```

#### nodegraph()
Returns the [Nodegraph](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg#Nodegraph) object.

### Classes

#### ColorWheelNode
Creates a new [ColorWheel node]() and adds it to the [nodegraph](https://hackmd.io/VIsuWHCySFWk6j2shR36zw).

##### Constructors
* ColorWheelNode()
* ColorWheelNode( name, pos )

The constructor *ColorWheelNode()* adds a new ColorWheel node to the node-graph. The name and position of the node are automatically filled.

The constructor *ColorWheelNode( name, pos )* adds a new ColorWheel node to the node-graph with the given *name* and at given *pos*. This constructor is used to save and restore a node-graph.

#### Dialog

##### Contructors
* Dialog( *text* )
* Dialog( *text* , *title* )

Creates and shows a Dialog with text. The title argument is optional.

Example:
```javascript
dialog = Dialog("Do you wish to continue?");
dialog.addButton("Continue"); // button 0
dialog.addButton("Cancel"); // button 1
clickedOption = dialog.wait();
if( clickedOption == 1 ) { // if clicked cancel button
    dialog.close();
    return;
}

dialog.setText("Downloading update...");
clickedOption = dialog.wait();
```





##### addButton( text )

```javascript
dialog = Dialog("Do you wish to continue?");
dialog.addButton("Continue");
dialog.addButton("Cancel");
clickedOption = dialog.wait(); // returns the button index when clicked
if( clickedOption == 1 ) { // clicked cancel button
    dialog.close();
    return;
}
```

##### addButton( text, functionHandler )

Example:
```javascript
function onOkButton()
{
    dialog.close();
}

dialog = Dialog("Downloading update...");
dialog.addButton( "Ok", onOkButton );
```

##### setProgress( percent )
Progress value needs to be between 0 and 1.
To hide the progress bar set a negative value (< 0).
To show a running progress set a value bigger than 1 (> 1).

##### setTitle( title )
set empty text to hide
##### setText( text )
set empty text to hide
##### wait()
Returns only when a button is clicked. The returned
value is the index of the clicked button.
##### close()
Closes and hides the dialog.


#### Dir
##### cd( dirName )
Enters directory *dirName*.
Returns true if successfull.

##### exists( name )
*name* is a file or directory name.
Returns true if file/dir exists.

##### size( name )
Returns the file size of the given file *name*.
Returns -1 if the file does not exist.

##### delete( name )
Deletes the file or directory with given *name*.

##### makeDir( name )


#### Download
Contructors:
* Download( dir, url )

Starts a downloads the specified ''url'' to the given ''dir''.

##### progress()
Returns the downloaded data size in bytes.

##### status()
Return an integer, that can be either 1, 2 or 3:
1. in progress
2. completed
3. failed

##### cancel()
Cancels the running download.


#### FootageNode

##### Constructors
*FootageNode( source )
*FootageNode( source, pos, name )

*source* is a video filename or a list of filenames of images (image sequence).
*pos* is a vector with 2 numbers.

```javascript
node = FootageNode( "C:\MyVideos\sun.mp4" );
```

See also [[#Node|Node class]].

#### Move2DNode

##### Constructors
* Move2DNode()
* Move2DNode( name, pos )

The constructor *Move2DNode()* adds a new Move2D node to the node-graph. The name and position of the node are automatically filled.

The constructor *Move2DNode( name, pos )* adds a new Move2D node to the node-graph with the given *name* and at given *pos*. This constructor is used to save and restore a node-graph.


#### Nodegraph

The [nodegraph() function](# Functions) returns a Nodegraph object.

##### setTranslation( x, y )
Translates the node-graph view to position ''x,y''.

#### Node

*Node* is the base class for all Mewa nodes, like [[#FootageNode]] and [[#ShaderNode]].


##### setName( name )
Sets the given ''name'' to the node. If the name already exist, a number is added at the end of the name
in order to make it unique.

##### setPos( x, y )


##### setHelpPage( url )

[panel image]

Use this function associate a help page to a node. The help page is url link.
The link is opened in the system web browser when the user clicks [help button] located at the top of node parameters window.


#### ShaderNode

##### Constructors
* ShaderNode( glslCode, nameHint )
* ShaderNode( glslCode, name, pos )

Creates a ShaderNode, with the given *glslCode*, and adds it to the node-graph.

*nameHint* is the name given to the node while generating a unique name for the node. 
If there is already a node with name *nameHint* a number will be added at the end of the *nameHint* to make it unique.

If *pos* is not provided the node will be placed at a "best guess" position.

The best way to learn on how to create shader nodes is to look at examples.
Mewa web store provides many scripts with it's source available. One example is [Ether](https://mewatools.com/webstore/index.php?view=Ether)

To fill the node's panel use the functions [*addFloatControl*](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#addFloatControl-variableName--defaultValue-), [*addVec2Control*](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#addVec2Control) and [*addColorControl*](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#addColorControl-variableName-).
Each of those functions adds one row to the node's panel, starting from the bottom.

##### Controls

Controls are graphical widgets used to change the value of input variables in the shader program. There are 3 different control types:
* *addFloatControl* connects to a input variable of type *float*
* *addVec2Control* connects to a input variable of type *vec2* 
* *addColorControl* connects to a input variable of type *vec3*

By default the controls will show the name of the variable as a text label. The label text can be modified by through the function:
* setName( name )

The control name should be unique within the node as the *name* can be used in the control search.

##### addFloatControl( variableName , defaultValue )
Adds a GUI control to the node [parameters window](https://hackmd.io/VIsuWHCySFWk6j2shR36zw?view#Parameters-window). The GUI control changes the value
of a variable in the shader program. The variable is of *float* data type.

*variableName* is the name of variable in the shader source that will be controlled.

![](https://i.imgur.com/FRnroxw.png)*Float control*

Returns a [FloatControl](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#FloatControl) object.

##### addVec2Control( variableName, defaultValues )

![](https://i.imgur.com/bF81GSl.png)*Vec2 Control*

Returns a [Vec2Control](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#Vec2Control) object.


##### addColorControl( variableName )
This function creates a [ColorControl](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#ColorControl) connected to variable with name ''variableName'' and initialized with black color (0,0,0).
See more at [ColorControl](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#ColorControl).

##### addColorControl( variableName, gray )
''gray'' argument is a number.
This function creates a [ColorControl](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#ColorControl) connected to variable with name ''variableName'' and initialized with ''gray'' value set on the three channels R,G and B.

##### addColorControl( variableName, red, green, blue )



The color control has 3 parameters. Clicking on the color button expands to show the 3 parameters.

##### setInputMapping( argIndex, mapping )
The *argIndex* is the number of the input argument passed to *mainImage* function inside the GLSL code.
The *mapping* should be ***iResolution***, ***"iChannel0"*** or ***"iChannel1"***. 


* An example of a node using **setInputMapping(0, "iResolution")** is [Ether](https://mewatools.com/webstore/index.php?view=Ether). This example uses the input coordinates passed into ''fragCoord'' in ''mainImage( out vec4 fragColor, in vec2 fragCoord )'' to generate a procedural image. Because "iResolution" option fills the entire viewport using ''fragCoord'' values that go always from 0 to 1, this option is mostly used to generate images.
* An example of a node using **setInputMapping(0, "iChannel0")** is [HexPixelate](https://mewatools.com/webstore/index.php?view=HexPixelate). The *iChannel0* option automatically adds an input port to the node. to connect an input image. The input coordinates ''fragCoord'' passed into ''mainImage( out vec4 fragColor, in vec2 fragCoord )'' cover only the input image. Also, note that ''fragCoord'' coordinates can have any range of values within the 0 to 1 limits. Use the texture size in variable ''iChannelResolution[0]'' to get, always, a 0 to 1 range in the ''fragCoord'' input variable. The ''iChannel0'' option is aminly aimed at the creation of image processing nodes, taking an input image for processing and outputing the result. 
* An example using **setInputMapping(0, "iChannel0")** and **setInputMapping(1, "iChannel1")** can be found in [OverlayBlend](https://mewatools.com/webstore/index.php?view=OverlayBlend). This option is mostly used to merge 2 images. It adds 2 input ports to the node. When using the ''iChannel0+iChannel1'' option make sure to be use ''mainImage( out vec4 fragColor, in vec2 fragCoordA, in vec2 fragCoordB )'' function in your shader source to access the texture coordinates of both images. Use the texture size in variable ''iChannelResolution[0]'' to get, always, a 0 to 1 range in the ''fragCoord'' input variable.


##### setFilter( channel, filter )
Options are Nearest, Linear or Mipmap
##### setWrap( channel, filter )
Options are Clamp or Repeat.

##### setFlip( channel, filter )
Options are NoFlip, HorizontalFlip or VerticalFlip.

#### ColorControl

![](https://i.imgur.com/auWlg9i.png)*Color Control*

Create a color control initialized with red color. ''uColor'' is the name of the ''vec3'' uniform variable in the glsl shader code.

```javascript
parameter = node.addColorControl("uColor", 0.8, 0.2, 0.2 );
```

Color control has 3 parameters, one for each color channel.

##### setName( name )
Sets the name of this control.
*name* is shown in the control as a text label.

See also [Controls section](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#Controls).

#### FloatControl

The code below, taken from [Ether.mw](https://mewatools.com/webstore/index.php?view=Ether), shows how a FloatControl is used.
The function ''addFloatControl'' creates a control, adds it to the node panel and returns the control for further setup.
```javascript
parameter = node.addFloatControl("uDelta", 2.5);
parameter.setName("Delta");
parameter.setStep(0.01);
parameter.setRange(-2, 7);
```

##### setRange( min, max )
Sets a minimum and maximum value a parameter can have.
To disable min and max, letting the UI control to reach any value set the same value for min and max (min == max).
##### setStep( increment )
Adjust the step value to make a parameter increase faster or slower with the mouse movement.
##### setName( name )
Sets the name of this control.
*name* is shown in the control as a text label.

The control name should be unique within the node as the ''name'' can be used in the control search.


#### Vec2Control

##### setName( name )
Sets the name of this control.
''name'' is shown in the control as a text label.

See also [Controls](https://hackmd.io/akGwvXj5QHSWS4m-6K8ggg?view#Controls).
