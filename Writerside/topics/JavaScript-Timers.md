# JavaScript Timers

## Abbreviations {collapsible="true"}

- \*[HOF]: Higher Order Functions

## Introduction {collapsible="true" default-state="expanded"}

In this subunit, we'll learn about a JavaScript function called **timers**. We're teaching you about timers both because
they are useful, and to shed some light on a category of JavaScript functions called callback functions. You'll be using
**callback functions** regularly as you write code. They are **functions that are passed as an argument to a second
function and execute while that second function is running, or after it completes**. That might be hard to wrap your
head
around at the moment, but by the end of this subunit, it should make more sense.

Timers will execute the function they are passed after a certain amount of time. For instance, if you want a smiley face
pop up to appear on-screen after two seconds, you pass a function to pop up an image and tell the timer to wait two
seconds. Because a timer's functionality is simple, we think they are a great tool to focus on while learning how
callbacks work.

If that's still a bit confusing, don't worry. You'll finish up this subunit with hands-on practice, and the best way to
learn is through actively doing something.

### Goals

- Understand the terms first class functions and higher order functions (HOF)
- Learn how to use and build your own callbacks
- Learn how to manipulate timers in JavaScript

## First-Class Functions {collapsible="true" default-state="expanded"}

- Functions in JavaScript are quite flexible because they are essentially treated just like other data types.
- And as you already know, you can assign functions to variables.
- For example, you can pass functions as arguments to other functions

```javascript
function takeAFunction(anotherFunc) {
  return anotherFunc(); // calling the parameter as a function }
}
let sayHi = function () {
  console.log('hello');
};
```

This is what we mean by first-class functions!

## Higher Order Functions {collapsible="true" default-state="expanded"}

A function is a HOF if it does at least one of the following:

- Accepts another function as a parameter
- Returns another function
- HOFs are a general concept in mathematics, not just JavaScript. However, they are pretty straightforward!

```javascript
function myHOF() {
  return function () {
    console.log('Returning this function also makes me a HOF!');
  };
}
```

## Callbacks {collapsible="true" default-state="expanded"}

Now that we know about first-class functions and HOFs, we finally know how to define callback functions!

```javascript
function markWahlberg(animal, callback) {
  console.log(`Hey ${animal}, how you doin'?`);
  callback();
}

function marksCallback() {
  console.log('Say hi to your mother for me, alright?');
}
```

Simply put, a callback is a (first-class) function that gets passed as a parameter to another function (a HOF).

The HOF will invoke the callback at some point.

```javascript
markWahlberg('chicken', marksCallback);
```

### Why callbacks?

- The callback can reduce repetition and re-definition of functions
- They are commonplace with more advanced array methods!

### An example

Imagine you are building a simple calculator, let’s start with some basic functions

```javascript
function add(a, b) {
  return a + b;
}
function subtract(a, b) {
  return a - b;
}
function multiply(a, b) {
  return a * b;
}
function divide(a, b) {
  return a / b;
}
```

This seems great, but:

- What happens when we want to do other operations like square roots
- What happens if we want to do multiple operations with a and b like a _ b + b _ a?
- We need to keep defining new functions each time!

### Using a callback

```javascript
function doMath(a, b, callback) {
  return callback(a, b);
}
doMath(10, 20, function (first, second) {
  return first + second;
});
doMath(5, 10, function (first, second) {
  return (first * second) / second + first;
});
doMath(5, 5, add); // 10
doMath(5, 5, subtract); // 0
```

<seealso>
[![MDN Web Docs](https://img.shields.io/badge/MDN_Web_Docs-black?style=flat&logo=mdnwebdocs&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) |
[![W3 Schools](https://img.shields.io/badge/W3Schools-6DA55F?style=flat&logo=w3c&logoColor=white)](https://www.w3schools.com/js/default.asp)
</seealso>
