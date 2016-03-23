# JavaScript Functions

Definition: Functions are "self contained" modules of code that accomplish a specific task. Functions usually "take in" data, process it, and "return" a result. Once a function is written, it can be used over and over and over again. Functions can be "called" from the inside of other functions.

## Function Types
Regular Ole' Function
```
function sayHello(name) {
	return 'Hello ' + name;
}

sayHello();
```

Constructor Pattern
```
function Person(name) {
    this.name = name;
    this.sayHello = function() {
        return “Hello, my name is “ + this.name;
    }
}

var me = new Person(“Adam”);
me.sayHello();
```

Prototype Pattern
```
function Friend(name) {
	this.name = name;
}

Friend.prototype.sayName = function() {
	return “My friend's name is “ + this.name;
}

var billy = new Friend('Billy');
billy.sayName();
```

Factory Pattern
```
function Animal(name) {
	return {
		run: function() {
			return name + “ is running!”
		}
	}
}
```

## Let's Draw on Canvas
First, we need to create the canvas to be able to draw on it.
```
<canvas id=“canvas”></canvas>
```
Now it's JavaScript from here on!
```
var canvas = document.getElementById(“canvas”);
var context = canvas.getContext(“2d”);
```
Let's give it a width and height
```
var canvas = document.getElementById(“canvas”);
canvas.width = 800;
canvas.height = 800;
var context = canvas.getContext(“2d”);
```
Now let's make that into a function
```
function draw() {
  var canvas = document.getElementById(“canvas”);
  canvas.width = 800;
  canvas.height = 800;
  var context = canvas.getContext(“2d”);
}
```
We want to actually show an actual object, so let's fill in the object like a box
```
function draw() {
  var canvas = document.getElementById("canvas");
  canvas.width = 800;
  canvas.height = 800;
  var context = canvas.getContext("2d");
  context.fillRect(10,10, 100, 200);
}
```

Finally, it just needs to be added to the page
```
function draw() {
  var canvas = document.getElementById("canvas");
  canvas.width = 800;
  canvas.height = 800;
  var context = canvas.getContext("2d");
  context.fillRect(10,10, 100, 200);
}

window.onload = draw();
```
Add another color to it using the fillStyle() method
```
function draw() {
  var canvas = document.getElementById("canvas");
  canvas.width = 800;
  canvas.height = 800;
  var context = canvas.getContext("2d");
  context.fillStyle = "blue";
  context.fillRect(10,10, 100, 200);
}

window.onload = draw();
```
## Let's draw some other shapes!
We will begin with a triangle. First create the triangle function.
```
function triangle() {
	var canvas = document.getElementById(“canvas”);
	var context = canvas.getContext(“2d”);
	canvas.width = 400;
	canvas.height = 400;
}
```
Now change the onload function to take the triangle function.
```
window.onload = triangle();
```
Now that we have our canvas, let's start to draw lines on the canvas to create our triangle.
```
function triangle() {
	var canvas = document.getElementById(“canvas”);
	var context = canvas.getContext(“2d”);
	canvas.width = 400;
	canvas.height = 400;

	context.beginPath();
	context.moveTo(75, 50);
}
```
Now that we have the path where we will start drawing, we can start to add our lines.
```
function triangle() {
	var canvas = document.getElementById(“canvas”);
	var context = canvas.getContext(“2d”);
	canvas.width = 400;
	canvas.height = 400;

	context.beginPath();
	context.moveTo(75, 50);
	context.lineTo(100, 75);
	context.stroke();
	context.lineTo(100, 25);
	context.stroke();
}
```
Now we can draw the last line to create the triangle.
```
function triangle() {
	var canvas = document.getElementById(“canvas”);
	var context = canvas.getContext(“2d”);
	canvas.width = 400;
	canvas.height = 400;

	context.beginPath();
	context.moveTo(75, 50);
	context.lineTo(100, 75);
	context.stroke();
	context.lineTo(100, 25);
	context.stroke();
	context.lineTo(75, 50);
	context.stroke();
}
```
To fill in the triangle we can use the fill method.
```
function triangle() {
	var canvas = document.getElementById(“canvas”);
	var context = canvas.getContext(“2d”);
	canvas.width = 400;
	canvas.height = 400;

	context.beginPath();
	context.moveTo(75, 50);
	context.lineTo(100, 75);
	context.stroke();
	context.lineTo(100, 25);
	context.stroke();
	context.lineTo(75, 50);
	context.stroke();
	context.fill();
}
```
Let's do the same thing, but this time we will create a pyramid.
```
function pyramid() {
	var canvas = document.getElementById(“canvas”);
	var context = canvas.getContext(“2d”);
	canvas.width = 400;
	canvas.height = 400;
}
```
Remember to change the unload function to pyramid now.
```
window.onload = pyramid();
```
Let's now move the cursor to where we want it to be.
```
function pyramid() {
	var canvas = document.getElementById(“canvas”);
	var context = canvas.getContext(“2d”);
	canvas.width = 400;
	canvas.height = 400;

	context.beginPath();
	context.moveTo(200, 0);
}
```
Now we can begin drawing our shape.
```
	context.lineTo(0, 400);
	context.stroke();
	context.lineTo(400, 400);
	context.stroke();
	context.lineTo(200, 0);
	context.stroke();
	context.fillStyle = “orange”;
	context.fill();
```
## Emojis!
Let's draw some emojis. We can begin with a happy face!
```
function smileyFaceEmoji() {
	var canvas = document.getElementById(“canvas”);
	var context = canvas.getContext(“2d”);
	canvas.width = 500;
	canvas.height = 500;
}
```
Remember to change unload to this function
```
window.onload = smileyFaceEmoji();
```
Now let's draw our face
```
context.beginPath();
context.arc(200, 200, 200, 0, Math.PI*2, true);
```
Cool huh! Next comes the eyes
```
context.moveTo(235, 225);
context.arc(225, 225, 10, 0, Math.PI*2, true);
context.moveTo(285, 225);
context.arc(275, 225, 10, 0, Math.PI*2, true);
```
Then the mouth!
```
context.moveTo(250, 275);
context.arc(250, 275, 50, 0, Math.PI, false);
context.moveTo(250, 275);
context.lineTo(200, 275);
context.stroke();
```
## Exercises
1. Draw any kind of emoji.
2. Draw your initials.
