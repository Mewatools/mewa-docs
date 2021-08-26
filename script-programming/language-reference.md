---
title: language-reference.md
tags: mewa-user-guide
description: Mewa - Video Creator & Compositor
---


### Language Reference

Mewa programming language, although resembling a lot like javascript, does not follow any programming language specfication.
It was designed to answer Mewa application requirements on performance and ease of use.
 
The language syntax might change in order to match future quirements or users preferences.

:::info
information message container
:::

#### Data Types
All numbers in Mewa are stored as floating-point.

Booleans true and false are stored as numbers 1.0 and 0.0.

Strings are represented by text within quotation marks, as shown below:

```javascript
myString = "Hello";
```

#### *if* Conditionals

```javascript
if(x == 0) 
{
    print('Zero')
}
else
{
    print('Non zero')
}
```

#### *while* Loops

```javascript
while( download.inProgress() ) {
    dialog.setProgress( download.progress() );
}
```

#### *do-while* Loops

```javascript
i=0;
do {
    // ...
    i+=1;
} while( i < 3 );
```
