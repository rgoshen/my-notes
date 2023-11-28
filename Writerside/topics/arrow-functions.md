# arrow functions

![javascript](javaScript.jpeg)

## Introduction {collapsible="true" default-state="expanded"}

In this subunit, you'll learn how this symbol => will make your life a lot easier. This symbol is called a **fat
arrow (=>)**, and it is a shorthand way to write functions and craft simpler code. In the coming videos and resource
we'll teach you exactly how to use fat arrows and arrow functions, some of the unexpected things they can do, and their
shortcomings.

## What are they {collapsible="true" default-state="expanded"}

- Arrow functions are shorthand for function expressions
- They cannot be named, and they only work as function expressions.
- They are ideal for shortening callbacks.

```javascript
[1, 2, 3].forEach(function (n, idx) {
  console.log(n, idx);
});
```

is the same as

```javascript
[1, 2, 3].forEach((n, idx) => {
  console.log(n, idx);
});
```

### Another Arrow Function

```javascript
[1, 2, 3, 4, 5].fiIter(function (n, idx) {
  return n % 2 === 0;
});
```

is the same as

```javascript
[1, 2, 3, 4, 5].fiIter((n, idx) => {
  return n % 2 === 0;
});
```

### More Arrow Functions

Arrow Functions have an implicit return if you leave out the curly braces

```javascript
/* square everything */
let nums = [1, 2, 3];
let arrSquared = nums.map((n) => n ** 2); // [1, 4, 9]
```

## Gotcha with Arrow Function {collapsible="true" default-state="expanded"}

You still need a return if it's not on one line!

```javascript
const multiply = (a, b) => {
  return a * b;
};
```

You will sometimes see () around an arrow function - especially with modern frameworks!

```javascript
const multiply = (a, b) => a * b;
```

If you want to return an object, make sure it's wrapped in () or on more than one line!

```javascript
const makeInstructor = (name) => {
  name: 'Colt';
};
makeInstructor(); // undefined

const makeInstructor2 = (name) => ({ name: 'Colt' });

makeInstructor2(); // {name: "Colt"}
```

## Arrow Functions and this {collapsible="true" default-state="expanded"}

Arrow Functions do not have their own **this** context. If your function uses the keyword **this**, be wary!

You should not be using arrow functions:

- In an object method
- When you need your own keyword **this**

### Arrow Functions & this - no no's

Do not use arrow functions inside of objects!

```javascript
const student = {
  firstName: 'Melissa',
  sayHi: () => {
    return 'Hello ' + this.firstName;
  },
};

student.sayHi(); // Hello undefined
```

The keyword **this** refers to the global object (window/global) not the student object - that's not good!

## Arrow Functions Usefulness {collapsible="true" default-state="expanded"}

Use arrow functions when you **don't** want the keyword **this** that a function normally creates.
Arrow functions are a replacement for the **bind** function in the example below.

```javascript
const student = {
  firstName: 'Melissa',
  sayHi: function () {
    setTimeout(() => {
      console.log('Hello ' + this.firstName);
    }, 1000);
  },
};

student.sayHi(); // Hello Melissa
```

<seealso>
[![MDN Web Docs](https://img.shields.io/badge/MDN_Web_Docs-black?style=flat&logo=mdnwebdocs&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) |
[![W3 Schools](https://img.shields.io/badge/W3Schools-6DA55F?style=flat&logo=w3c&logoColor=white)](https://www.w3schools.com/js/default.asp)
</seealso>
