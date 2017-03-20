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
```

### Example of Object Modification Resulting in a New Object, not a Self-modified Object

```
// Set item equal to a new string object
var item = 'test';

// itemRef new refers to the same string object
var itemRef = item;

// Concatenate some new text onto the string object
// NOTE: This creates a new object and does not modify
// the original object.
item += 'ing'

// The values of item and itemRef are NOT equal, as a whole
// new string object has been created
console.log(item != itemRef);
```

### Example of How the Variable Scope in Javascript works

```
// Set a global variable, foo, equal to test
var foo = 'test';

// Within an if block
if(true){
	// Set foo equal to 'new test'
	// NOTE: This still belongs to the global scope!
	var foo = 'new test';
}

// As we can see here, as foo is new equal to 'new test'
console.log( foo === 'new test' );

// Create a function that will modify the variable foo 
function test(){
	var foo = 'old test';
}

// However, when called, 'foo' remains within the scope
// of the function
test();

// Which is confirmed, as foo is still equal to 'new test'
console.log( foo === 'new test' );
```


### Example of Implicit Globally Scoped Variable Declaration
```
// A function in which the value of foo is set
function test(){
	foo = 'test';
}

// Call the function to set the value of foo
test();

// We see that foo is now globally scoped
console.log( window.foo == 'test' );
```

### Example of Using Function Within Context and Then Switching Context to Another Variable

```
function setFoo(fooInput){
	this.foo == fooInput;
}

var foo = 5;
console.log( 'foo at the window level is set to: '+ foo');

var obj = {
	foo : 10
};

console.log( 'foo inside of obj is set to :' + obj.foo );

// This will change window-level foo
setFoo(15);
console.log( 'foo at the window level is set to: '+ foo');

// This will change the foo inside the object
obj.setFoo = setFoo;
obj.setFoo(20);
console.log(' foo inside of obj is now set to '+ obj.foo');
```

### Examples of Changing the context of functions

```
// A simple function that sets the color style of its context
function changeColor(color){
	this.style.color = color;
}

// Calling it on the windows object, which fails, since it doesn't
// have a style object
chageColor('white');

// Create a new div element, which will have a style object
var main = document.createElement('div');

// Set its color to black, using the call method
// The cal method sets the context with the first argument
// and passes all the other argument as arguments to the function
chageColor.call(main, 'black');

// Check results using console.log
// The output should say 'balck'
console.log(main.style.color);

// A function that sets the color on the body element
function setBodyColor(){
	// The apply method sets the context to the body element
	// with the first argument, and the second argument is an array
	// of argument that gets passed to the funcion
	changeColor.apply( document.body, arguments );
}

// Set the background color of the body to balck

setBodyColor('black');
```

### Two Example of How Closures Can Improve the Clarity of your code

```
// Find the element with an ID of 'main'
var obj = document.getElementById('main');

// Change its border styling
obj.style.border = '1px solid red';

// Initialize a callback that will occur in one second
setTimeout(function(){
	//Which will hide the object
	obj.style.display = 'none';
}, 1000);

// A generic function for displaying a delayed alert message
function delayedAlert(msg, time){
	// Initialize an enclosed callback
	setTimeout(function()
	{
		//Which utilizes the msg passed in from the enclosing function
		console.log(msg);
	},time
	);
}

// Call the delayedAlert function with two arguments
delayedAlert('Welcome!', 2000);

setTimeout('otherFunction()', 1000);
```

### Example of Function Currying Using Closures

```
// A function that generates a new function for adding numbers
function addGenerator(num){
	// Return a simple function for adding two numbers
	// with the first number borrowed from the generator
	return function(toAdd){
		return num + toAdd
	};
}

// addFive now contains a function that takes one argument,
// adds five to it, and returns the resulting number
var addFive = addGenerator(5);

// We can see here that the result of the addFive function is 9,
// When passed an argument of 4
console.log( addFive(4) == 9);





