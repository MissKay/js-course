# Let's Build a Hex Clock
 We are going to take what we learned a step further and create a hex clock.
 What is a hex clock you say? A hex clock is a timer that changes a web pages
 color each second. To start let’s create a function that gets the time of day.

 ## getTimeOfDay Function
```
function getTimeOfDay() {
  var date = new Date()
  var hour = date.getHours()
  var min = date.getMinutes()
  var sec = date.getSeconds()
  document.body.innerHTML = ‘’ + hour + min + sec
    return ‘’ + hour + min + sec
}
 ```

JavaScript has many handy utilities to make things a little easier
for programmers. One of those utilities is the Date object. As you may have noticed we
instantiate a Date object with the new keyword. Once instantiated we can
begin to use methods that allow use to retrieve data such as what the current hours,
minutes, and seconds are. After getting that data I am then setting the innerHTML
property of the body to equal it. I am returning a string of hour, min, and
sec because we will need it later. Now every time we call this function we will get a new
date object and from that, we will get the new hours, minutes, and seconds.

Next, let’s make a function that creates a color based
on the time we get from the getTimeOfDay function.

 ## getColor Function

```
function getColor(time) {
  var color = '#' + time
  document.body.style.backgroundColor = color
}
```

This is simple enough. We are passing in a time parameter and adding a hash to
it to make the variable color into a hexadecimal. Hexadecimals are one of the
ways of referencing colors. We then set the document’s body background color
property to that hexadecimal.Now all we have to do is wire this up so that the
background changes each second. Here we will use another handy global function called setInterval.

## setInterval Function

```
 setInterval(function() {
  return getColor(getTimeOfDay())
}, 1000)
```

If you are working on this project early in the morning, like before ten,
then you will notice that you don’t have any color on the screen. Do you know why?
The reason is when the Date object gets the hours and it’s before ten, it will pass
back 9. Not 09, just plain 9. That means that we don’t have a hexadecimal, we
have a number fewer than 6 characters in length. I say fewer because when any
number is less than ten we only get back one number. We need the variables hour, min,
and sec to be composed of two numbers even when they are less than ten. To do
that we will update the getTimeOfDay function. We will use some functional
programming to achieve this by using JavaScripts map function.

```
function getTimeOfDay() {
  var date = new Date()
  var hour = date.getHours()
  var min = date.getMinutes()
  var sec = date.getSeconds()
  // — Add below
  var array = [hour, min, sec]
  var newArray = array.map(function(time) {
  var newTime = time < 10 ? ‘0’ + time : String(time)
    return newTime
  })
  hour = newArray[0]
  min = newArray[1]
  sec = newArray[2]
  // — Add above
  document.body.innerHTML = hour + min + sec
  return hour + min + sec
}
```

We kind of made a quantum leap by adding the map function so let me tell you what’s happening. We are
creating a new array that is composed of the time values. We are iterating
over that array using the map function and storing those values in a new array.
When we iterate over all the values in the array we are passing each value
in as the variable time. Then, inside of the callback function we are creating a new time.
Here we use the ternary operator to check if the time value is less than ten. If that
statement is true, we return the time with a zero in front. If that statement is false, we return
the time back as a string. Afterward, we set hour, min, and sec to equal the values in newArray.
When you put it all together, this is what you get, with some minor adjustments:

```
function getTimeOfDay() {
  var date = new Date()
  var hour = date.getHours()
  var min = date.getMinutes()
  var sec = date.getSeconds()
  var array = [hour, min, sec]
  var newArray = array.map(function(time) {
  var newTime = time < 10 ? ‘0’ + time : String(time)
    return newTime
  })
  hour = newArray[0]
  min = newArray[1]
  sec = newArray[2]
  document.body.innerHTML = hour + min + sec
  return hour + min + sec
}

function getColor(time) {
  var color = '#' + time
  document.body.style.backgroundColor = color
}

function compose(f, g)
  return f(g())
}

function start() {
  setInterval(function() {
    compose(getColor, getTimeOfDay)
  }, 1000)
}

window.onload = start
```

As you will see here I added a compose function and put our setInterval
inside of a start function so that when the window is loaded the start function will kick it
all off. This is not much different, just a bit more functional in nature.
