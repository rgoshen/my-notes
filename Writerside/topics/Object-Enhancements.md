# Object Enhancements

![javascript](javaScript.jpeg)

## Abbreviations {collapsible="true"}

- \*[JS]: JavaScript

## Introduction {collapsible="true" default-state="expanded"}

Objects are one of the most fundamental data structures in JavaScript, and you'll be working with them all the time. In
ES2015, a few nice enhancements were introduced so that you can accomplish some tasks writing less code. Let's explore
some of those newer object enhancements!

## Object Shorthand {collapsible="true" default-state="expanded"}

ES2015 provides quite a few enhancements for JS objects!

When the keys are the same name as the variable values, (this happens a lot), you don't have to repeat yourself.

```javascript
let firstName = 'Mary';
let lastName = 'Malarky';

// ES5 (Oldschool)

let instructor = {
  firstName = firstName,
  lastName = lastName,
};
```

```javascript
let firstName = 'Mary';
let lastName = 'Malarky';

// ES6

let instructor = {
  firstName,
  lastName,
};
```

## Object Methods {collapsible="true" default-state="expanded"}

A nice shorthand when a key in an object represents a function.

```javascript
// ES5

let instructor = {
  sayHello: function () {
    return 'Hello!';
  },
};
```

```javascript
// ES2015

let instructor = {
  sayHello() {
    return 'Hello!';
  },
};
```

## Computed Property Names {collapsible="true" default-state="expanded"}

ES2015 allows us to create an object with a key that JavaScript can compute at definition.

Here’s what we mean by that!

```javascript
// ES5

let firstName = 'Mary';
let instructor = {};
instructor[firstName] = "That's me!";
instructor.Mary; // "That's me!"
```

```javascript
// ES2015

let firstName = 'Mary';
let instructor = {
  [firstName]: "That's me!",
};
instructor.Mary; // "That’s me!"
```

## Current Usage {collapsible="true" default-state="expanded"}

- These new shorthand methods are everywhere!
- Object shorthand and methods allow for writing less code
- Computed property names are everywhere in modern web frameworks.

## Computed Property Names in the Wild {collapsible="true" default-state="expanded"}

- This appears when you work with multiple inputs or DOM elements, and you want to change the value in an object based
  on
  a specific interaction,
- It's impossible to know upfront what key you are changing in the object without hard coding the key, so instead we can
  use the **event** object for a browser interaction.

```javascript
function changeValueInObj(obj, event) {
  return {
    ...obj,
    [event.target.name]: [event.target.value],
  };
}
```

<seealso>
[![MDN Web Docs](https://img.shields.io/badge/MDN_Web_Docs-black?style=flat&logo=mdnwebdocs&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) |
[![W3 Schools](https://img.shields.io/badge/W3Schools-6DA55F?style=flat&logo=w3c&logoColor=white)](https://www.w3schools.com/js/default.asp)
</seealso>
