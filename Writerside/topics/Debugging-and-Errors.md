# Debugging and Errors

## Introduction {collapsible="true" default-state="expanded"}

In this subunit, we'll go over **debugging in JavaScript**. When you write code, sometimes it's not going to work
correctly. **Debugging** is the process of identifying what is going wrong with your code and fixing it. You will spend
a considerable amount of time throughout your career debugging, especially in your early career. This can be a tedious
and time-consuming task, but debugging is also a fantastic opportunity to learn the ins and outs of your codebase and
how the application should function properly.

We'll show you some common errors in JavaScript, **how to read error messages**, and how to use **console.log** to help
you debug. We'll also teach you some of the native debugging tools in Google Chrome and how to handle errors using *
*try/catch**.

Fun fact, one supposed origin of the term "bug" dates back to the 1940s! Admiral Grace Hopper discovered her Harvard
Mark II was malfunctioning because a moth had gotten stuck inside the computer!

### Goals

- Define three of the most common errors in JavaScript and how to debug them
- Examine the Chrome Dev Tools for debugging
- Catch errors using try/catch/finally blocks
- Throw errors with specific messages

## Debugging {collapsible="true" default-state="expanded"}

- You are going to make mistakes!
- Let’s examine ways to better debug
- Let’s first examine some common errors

### SyntaxError

- You’ve seen this one before!
- You have to fix these right away!

```javascript
"awesome

function first ( {}

let = "nice!"
```

### ReferenceError

- Thrown when you try to access a variable that is **not defined**
- This does not mean **undefined**

```javascript
function sayHi() {
  let greeting = 'hi!';
}
sayHi();
greeting; // ReferenceError
```

### TypeError

- Trying to do something with a type that you can not
- Accessing properties on **undefined** or **null**
- Invoking (“calling”) something that is not a function

```javascript
'awesome'.splice(); // TypeError

let obj = {};

obj.firstName.moreInfo; // TypeError
```

### Two kinds of bugs

- An error is thrown — **easier**
- You did not get what you wanted — **harder**!

### A process for debugging

- Make assumptions
- Test assumptions
- Prove assumptions
- Repeat

### console.log

- Be mindful about what you print out
- Great for a sanity check
- Even better when you add parameters

```javascript
console.log('We made it!');
console.log('The value of x is --->', x);
```

## JavaScript Debugger {collapsible="true" default-state="expanded"}

- Watch execution of code and examine at any point
- Built into Chrome (other browsers have similar abilities)
- Can debug in-browser code or Node

### Starting debugger

View code or adding “breakpoints”:

**View** → **Developer** → **Developer Tools** → **Sources tab**

Click left of the line of code to add a blue breakpoint

Can put breakpoint into code itself:

```javascript
function myFunction() {
  let x = 1;
  debugger; // <-- will always stop here // rest of code follows ...
}
```

### Step Over

![step-over-outline](step-over-outline.png)
Run current line, but don’t debug into any function calls

### Step Into

![step-into-outline](step-into-outline.png)
Run current line, stepping into any function calls

### Step Out

![step-out-outline](step-out-outline.png)
Return from this function to caller

### Call Stack

![call-stack](call-stack.png)
Shows stack of function calls that got you here

### Scope

![scope](scope.png)
Shows the current value of variables

Can click to change value

## Tips to Avoid Bugs {collapsible="true" default-state="expanded"}

### Plan first

> Software and cathedrals are much the same — first we build them, then we pray.
>
> — _Sam Redwine, 1988_

### Keep it simple

> Everyone knows that debugging is twice as hard as writing a program in the first place. If you’re as clever as you can
> be when you write it, how > will you ever debug it?
>
> — _Brian Kernighan, The Elements of Programming Style_

(That’s a particularly excellent intermediate book, by the way)

### Common JavaScript Bugs

- == is very loose about comparisons (=== isn’t)
    - `7 == '7'`
- Objects & arrays are not equal to similar objects & arrays
    - `[1, 2, 3] !== [1, 2, 3]`
- Calling function with missing arguments makes those arguments **undefined**
- Calling function with extra arguments is ignored (the extra arguments are ignored).
- Getting a missing property from object/index from an array is **undefined**

### Good News

> If debugging is the process of removing bugs, then programming must be the process of putting them in.

> — _Edsger W. Dijkstra_

- Bugs are an opportunity to improve debugging skills & to learn something
- You will have lots of chances to practice this valuable skill!

## Error Handling {collapsible="true" default-state="expanded"}

- Sometimes errors cannot be avoided!
- This especially happens when working with external APIs / other people’s data
    - Connection failures
    - The API is down
- Instead of errors crashing our program, let’s handle them gracefully!

### Let’s “try” it out!

```javascript
functionThatDoesNotExist();
console.log('did we make it?');
```

```javascript
try {
  functionThatDoesNotExist();
} catch (err) {
  console.log('something went wrong!', err);
}

console.log('did we make it?');
```

Notice the important difference here!

### Introducing try / catch

```javascript
try {
  // place the code you would like to try to run
} catch (err) {
  // if an error occurs, run whatever code we place in here!
}
// keep going!
```

**try** and **catch** create block scope, so if you define a variable inside using **let** or **const** it will only
exist in that block.

The parameter to **catch** is optional, but we highly recommend using it, so you can see what the error is and any
information about it!

### Another Example

```javascript
function displayInitials(user) {
  let firstNameLetter = user.firstName[0].toUpperCase();
  let lastNameLetter = user.lastName[0].toUpperCase();
  return `Hello ${firstNameLetter}.${lastNameLetter}`;
}
```

What happens when we don’t pass in an object?

What happens when our object does not have the correct keys or values?

### Using try / catch

```javascript
function displayInitials(user) {
  let firstNameLetter;
  let lastNameLetter;
  try {
    firstNameLetter = user.firstName[0].toUpperCase();
    lastNameLetter = user.lastName[0].toUpperCase();
  } catch (e) {
    return 'Invalid input!';
  }
  return `Hello ${firstNameLetter}.${lastNameLetter}`;
}
```

Strive to only place code that will throw an error inside your try/catch block!

### When to use try/catch

Think about using try/catch when:

- The output of your program is unpredictable
- There is any chance that an unexpected error may occur
- You don’t want a tremendous amount of conditional logic

### Making your own errors!

You can actually create your own errors in JavaScript using the **throw** keyword

```javascript
console.log('an error is coming....');
throw 'What just happened?!?';
console.log('did we make it?');
```

### Exploring with try/catch

```javascript
console.log('an error is coming....');
try {
  throw 'Oh no!';
} catch (err) {
  console.log('what happened?', err);
}
```

All we see here is the string that we passed to throw with no information about the kind of error or where it happened.

### Throwing better errors

Instead of just using the **throw** keyword, you can make a new Error object using the **new** keyword.

```javascript
console.log('an error is coming....');
try {
  throw new Error('Oh no!');
} catch (err) {
  console.log('what kind of error?', err.name);
  console.log('what is the message?', err.message);
  console.log('where did it happen?', err.stack);
}
```

Notice that we get more information here including where the error occurred!

We’ll discuss what **new** does in much more detail later in the course, but for now you should use it when making your
own errors.

### When should you use this?

- any time you want to hide errors from a user
- any time you want to produce custom errors for your users’ benefit.
- it works as a nice fallback in areas of your code that could fail under unusual circumstances that were not foreseen
  during development
- it can hide overly technical error messages from users who would not understand them anyhow
- use it for portions of your code where you suspect errors will occur that are beyond your control

### When should you not use this?

If you know an error is going to occur, because in this case, you would want to debug the problem, not hide it.

You still have to debug on your own!

### finally

try/catch blocks come with another optional keyword **finally** which will execute code regardless if an error is thrown
or not

```javascript
try {
  undefined(); // this will throw a TypeError
} catch (err) {
  console.log('something went wrong!', err);
} finally {
  console.log("we're all done!");
}
```

You will rarely find yourself using this, but it’s good to know if you want to be explicit about what to run no matter
what in a try/catch block

<seealso>
[![MDN Web Docs](https://img.shields.io/badge/MDN_Web_Docs-black?style=flat&logo=mdnwebdocs&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) |
[![W3 Schools](https://img.shields.io/badge/W3Schools-6DA55F?style=flat&logo=w3c&logoColor=white)](https://www.w3schools.com/js/default.asp)
</seealso>
