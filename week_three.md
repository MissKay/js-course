# JavaScript In the DOM


What is the DOM? The DOM represents a document as a tree. The tree is made up of parent-child relationships, a parent can have one or many children nodes.

```
         HTML
  _________|_________
  |                 |
HEAD               BODY
  |                 |
TITLE              DIV
  |            _____|_____
My Site        |         |
```

We have already worked with the DOM before.

```
var canvas = document.getElementById('canvas');
```

Now let's take what we know and do something a little different. Instead of working on 'canvas' we are going to interact with the DOM directly. Let's first get the width and height of the DOM window.

```
var width = window.innerWidth;
var height = window.innerHeight;

var dimensions = document.createElement('P');
dimensions.textConent = width + ', ' + height;

document.appendChild(dimensions);
```
That was okay. Now let's do something that's a bit more interactive. This time we will get the x and y coordinates of the document and display those on the screen as the mouse hovers over the DOM.

```
document.body.style.width = '100vw';
document.body.style.height = '100vh';

document.body.addEventListener("mousemove", function(event) {
  var x = event.clientX;
  var y = event.clientY;
  document.body.innerHTML = x + ', ' + y;
});
```

Pretty neat huh? This was a bit better but we can do better. We can add some more functionality to the program so that the body color changes based on the x and y coordinates.
```
document.body.style.backgroundColor = 'rgb(' + x + ', ' + y + ', 300)';
```
Let's recap. There are many ways to interact with the DOM. We can add elements, add event listeners, and manipulate the style or any other part of the DOM based on the feedback we get from that data.

There are many more ways to interact with the DOM in fun and interesting ways. Let's take a look at what those other ways are. We are going to take what we learned a step further and create a hex clock. What is a hex clock you say? A hex clock is a timer that changes color each second. You will see. To start let's create a function that gets the time of day.
```
function getTimeOfDay() {
	var date = new Date();
	var hour = date.getHours();
	var min = date.getMinutes();
	var sec = date.getSeconds();
	document.body.innerHTML = '' + hour + min + sec;
	return hour + min + sec;
}
```
Now every time we call this function we will get a new date object and from that we will get the time.
Next let's make a function that creates a color based on the time.
```
function getColor(time) {
  var color = '#' + time;
  document.body.style.backgroundColor = color;
}
```
Now all we have to do is wire this up so that the background changes each second. Here we will use another handy global function called setInterval.
```
setInterval(function() {
  return getColor(getTimeOfDay());
}, 1000);
```
When you put it all together, this is what you get, with some minor adjustments:
```
function getTimeOfDay() {
  var date = new Date();
  var hour = date.getHours();
  var min = date.getMinutes();
  var sec = date.getSeconds();

  hour = hour < 10 ? '0' + hour : String(hour);
  min = min < 10 ? '0' + min : String(min);
  sec = sec < 10 ? '0' + sec : String(sec);

  document.body.innerHTML = hour + min + sec;
  return hour + min + sec;
}

function getColor(time) {
  var color = '#' + time;
  document.body.style.backgroundColor = color;
}

function compose(f, g) {
  return f(g());
}

function start() {
  setInterval(function() {
    compose(getColor, getTimeOfDay);
  }, 1000);
}

window.onload = start;
```

What do you think we can do next? You think we can make a drawing app with everything that we know. Let's see what we can do.

First let's create the canvas element.
```
var canvasEl = document.createElement('CANVAS');
canvasEl.id = 'canvas';
document.body.appendChild(canvasEl);

var canvas = document.querySelector('canvas');
var context = canvas.getContext('2d');
```
Now let's add some event listeners to the body element so that we now when to begin drawing the line and when to stop drawing the line.
```
document.body.addEventListener('mousedown', start);
document.body.addEventListener('mouseup', stop);
```
Next we can begin creating the functionality for the app, starting with the start function. Go!
```
function start(event) {
  var x = event.clientX;
  var y = event.clientY;

  context.beginPath();
  context.moveTo(x, y);
}
```
Now when we stop we want the line to stop and complete the drawing of the line.
```
function stop(event) {
  var x = event.clientX;
  var y = event.clientY;

  context.lineTo(x, y);
  context.stroke();
}
```
Lastly, whenever the window loads we want the canvas to resize based on the size of the window.
```
function sizeCanvas() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}

window.onload = sizeCanvas;
```
Now let's see it call come together.
```
var canvasEl = document.createElement('CANVAS');
canvasEl.id = 'canvas';
document.body.appendChild(canvasEl);

var canvas = document.querySelector('canvas');
var context = canvas.getContext('2d');

document.body.addEventListener('mousedown', start);
document.body.addEventListener('mouseup', stop);

function start(event) {
  var x = event.clientX;
  var y = event.clientY;

  context.beginPath();
  context.moveTo(x, y);
}

function stop(event) {
  var x = event.clientX;
  var y = event.clientY;

  context.lineTo(x, y);
  context.stroke();
}

function sizeCanvas() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}

window.onload = sizeCanvas;
```
