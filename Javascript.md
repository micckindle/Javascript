# Javascript

## Features, Functions, and Objects

### Example of Mulitple Variables Referring to a Single Object

```
// Set obj to an empty object
// (Using {} is shorter than 'new Object()')
var obj = {};

// objRef now refers to the other object
var refToObj = obj;

// Modify a property in thr original object
obj.oneProperty = true;

// We now see that the change is represented in both variables
// (Since they both refer to the same object)
console.log( obj.oneproperty === refToObj.oneproperty));

// This change goes both ways, since obj and refToObj are both references
refToObj.anotherProperty = 1;
console.log( obj.anotherProperty === refToObj.anotherProperty );
```