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

### Example of a self-Modifying object

```
// Create an array of items
// (Similar to 2-1, using [] is shorter than 'new Array()')
var item = ['one', 'two', 'three'];

// Create a references to the array of items
var itemsRef = items;

// Add an item to the original array
items.push('four');

// The length fo each array should be the same,
// since they both point to the same array object
console.log(items.length == itemsRef.length);
```

### Changing the Reference of Object While Maintaining Integrity

```
// Set items to an array (object) of strings
var item = ['one', 'two', 'three'];
// Set itemsRef to a reference to items
var itemsRef = items;

// Set items to equal a new object
item = ['new', 'array'];

// items and itemsRef new point to different objects.
// item point to ['new', 'array']
// itemRef point to ['one', 'two'E, 'three']
console.log( items !== itemRef );





