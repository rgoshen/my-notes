# this

![javascript](javaScript.jpeg)

## Abbreviations{collapsible="true"}

- \*[JS]: JavaScript

## Introduction {collapsible="true" default-state="expanded"}

In this subunit, we'll tackle the most confusing word in JavaScript—the
keyword **this**, this is only four letters, but it will take a whole subunit to
understand. Make a note; this is a favorite topic that interviewers love to quiz prospective employees about. We'll dive
deep into what the keyword this refers to and how you can easily determine its value.

### Goals

- Learn how to stop worrying and love the keyword **this**
- Explain what **.call** does
- Explain what **.bind** does
- Use **.call** and **.bind** to reassign the value of the keyword **this**

## This and Bind {collapsible="true" default-state="expanded"}

### This

> Sometimes when I'm writing JavaScript, I want to
>
> throw up my hands and say "this is bullshit!" but
>
> I can never remember what "this" refers too
>
>     Ben Halpern
>     @benhalpern

### Mystery of the Undefined Fluffy

_demo/fluffy.js_

```javascript
class Cat {
  constructor(name) {
    this.name = name;
  }

  dance(style) {
    return `Meow, I am ${this.name}` + ` and I like to ${style}`;
  }
}
```

_makes sense_

```javascript
let fluffy = new Cat('Fluffy');

fluffy.name; // "Fluffy"

fluffy.dance('tango'); // works!
```

_wtf?_

```javascript
let fDance = fluffy.dance;

fDance('salsa'); // error?
```

## JavaScript Functions {collapsible="true" default-state="expanded"}

In a sense, JavaScript doesn't have functions.

### Everything is called on something

```javascript
function whatIsThis() {
  console.log('this =', this);
}

let o = { myFunc: whatIsThis };

o.myFunc(); // get "this = o"

whatIsThis(); // wtf?
```

### Global Object

When you call a function on nothing...

... you call it on the "global object"

- In browser JS, that's **window** (the browser window)
- in Node.js, that's **global** (where some Node utilities are)

You relied on that, even if you didn't realize it!

```javascript
alert('Hi!');

window.alert('Hi!'); // -- same thing!
```

Therefore, a "function" called at the top level is the same as:

```javascript
window.whatIsThis();
```

### Undefined Fluffy

_demo/fluffy.js_

```javascript
class Cat {
  constructor(name) {
    this.name = name;
  }

  dance(style) {
    return `Meow, I am ${this.name}` + ` and I like to ${style}`;
  }
}
```

_so... what's happening here?_

```javascript
let fluffy = new Cat('Fluffy');

fluffy.name; // "Fluffy"

fluffy.dance('tango'); // works!

let fDance = fluffy.dance;

fDance('salsa'); // error?
```

```javascript
flufy.dance('tango');
```

- **Find** the **dance** method on fluffy
- **Call** the **dance** method on fluffy - yay!

```javascript
let fDance = fluffy.dance;
fDance('tango');
```

- **Find** the **dance** method on fluffy
- **Call** the **dance** method on the global window - ut oh!

### call

Sometimes, you'll need to say "call this function on this object"

That's what `call()` is for!

```javascript
let fDance = fluffy.dance;

// call on fluffy, passing "tango" as arg
fDance.call(fluffy, 'tango');

whatIsThis(fluffy); // this = fluffy
```

**NOTE:** **apply()**

There is a related function, `apply()`: for this, you can pass the list of arguments to the function as an array, rather
than passing one-by-one.

This used to be a crucial technique, since it was the only reasonable way to call a function that expected
several individual arguments where you already had those arguments in a list:

```javascript
Math.max(1, 2, 3); // Math.max expects individual arguments

let myNums = [1, 2, 3]; // If you already have an array...

Math.max.apply(null, myNums); // pass that array as individual arguments
// (don't care what this is, so pass 'null')
```

Nowadays, however, this is much easily done with the spread operator:

```javascript
Math.max(...myNums);
```

### Bind

You can "perma-bind" a function to a context

```javascript
fDance('tango'); // error -- this isn't the cat

fDance.call(fluffy, 'tango'); // ok but tedious to always docs
let betterDance = fDance.bind(fluffy);

betterDance('tango'); // ok -- bound so that 'this' is Fluffy
```

`bind` is a method on functions that returns a bound copy of the function

### Binding Arguments

You can also bind arguments to functions. That will bake them into the function.

```javascript
function applySalesTax(taxRate, price) {
  return price + price * taxRate;
}

// "null" for "this" means it doesn't matter what "thi" is
const applyCASalesTax = applySalesTax.bind(null, 0.0725);

applyCASalesTax(50); // 53.63
```

## Where This Comes Up {collapsible="true" default-state="expanded"}

### Callback on Methods

Want to have object method as callback:

```javascript
myBtn.addEventListener('click', fluffy.dance);
```

That won't work - browser will call **dance** on a global object. 😦

```javascript
myBtn.addEventListener('click', fluffy.dance.bind(fluffy));
```

That will work — when it calls that callback, it will always be on Fluffy!

### Pre-Binding Calls

Imagine we want three buttons which call **popUp**, but with different args:

_demo/buttons-meh.html_

```html

<button id="a">A</button>
<button id="b">B</button>
<button id="c">C</button>
```

_demo/buttons-meh.js_

```javascript
function popUp(msg) {
  alert('Secret message is ' + msg);
}

function handleClick(evt) {
  let id = evt.target.id;

  if (id === 'a') {
    popUp('Apple');
  } else if (id === 'b') {
    popUp('Berry');
  } else if (id === 'c') {
    popUp('Cherry');
  }
}

const get = document.getElementById.bind(document);

get('a').addEventListener('click', popUp.bind(null, 'Apple'));
get('b').addEventListener('click', popUp.bind(null, 'Berry'));
get('c').addEventListener('click', popUp.bind(null, 'Cherry'));
```

## Arrow Functions {collapsible="true" default-state="expanded"}

Arrow functions don’t make their own **this**

_demo/timeout.js_

```javascript
class Cat {
  constructor(name) {
    this.name = name;
  }

  superGreet() {
    alert(`#1: I am ${this.name}`); // works, obvs

    setTimeout(function () {
      alert(`#2 I am ${this.name}`); // ut oh
    }, 500);

    setTimeout(() => {
      alert(`#3: I am ${this.name}`); // yay!
    }, 1000);
  }
}

let kitty = new Cat('Kitty');
kitty.superGreet();
```

<seealso>
[![MDN Web Docs](https://img.shields.io/badge/MDN_Web_Docs-black?style=flat&logo=mdnwebdocs&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) |
[![W3 Schools](https://img.shields.io/badge/W3Schools-6DA55F?style=flat&logo=w3c&logoColor=white)](https://www.w3schools.com/js/default.asp)
</seealso>
