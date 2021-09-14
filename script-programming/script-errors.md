---
title: script-errors.md
tags: mewa-dev
description: Mewa - Video Creator & Compositor
---

# Script Errors

This page provides detailed information about scripting errors to help understand and solve these errors.

Tell us what errors you've found and let us help you find a better solution to your problem. Contact us (through [Discord](https://discord.gg/wZ884Bhm) or any other way)


## Errors


#### Error 190 : Cannot concatenate strings

The main performance penalty on script/expression execution are memory allocations and deallocations.
To avoid allocations and deallocations, Mewa strings are kept static.

Below is an example that raises this error.

```javascript
n=node("Add" + "0"); // error 190
```

:::info
:bulb: Suggested feature request:
```javascript
dinamicString = String("Add") + "0";
```
:::

#### Error 201 : Cannot assign arrays to variables

Assigning static arrays to variables is currently not allowed to prevent an perfomance hit caused by memory allocations.

The code below ilustrates an array assignment:
```javascript
defaultRadius = outputResolution() * [0.33, 0.33]; // error 201 
node.addMouseControl("uRadius", defaultRadius );
```
Instead, array operations should be done inline, as shown below: 
```javascript
Arrays need to be used inline:
node.addMouseControl("uRadius", 
    outputResolution() * [0.33, 0.33]
);
```

