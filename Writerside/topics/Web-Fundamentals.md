# Web Fundamentals

## Abbreviations {collapsible="true"}

- \*[CSS]: Cascading Style Sheet
- \*[HTML]: Hypertext Markup Language
- \*[js]: JavaScript

## Introduction {collapsible="true" default-state="expanded"}

The **software engineering techniques** we’ll teach you in this course build on **web fundamentals** like **HTML, CSS,
and JavaScript**. We want to make sure you understand the basics of these languages before we get into more advanced
techniques. Depending on your knowledge level, this unit could be mostly reviewed. Every page on the internet uses some
combination of HTML, CSS, and JavaScript—so once you learn how to use these languages effectively, the possibilities
are endless. Employers will want you to have knowledge of these languages—daily work will use these skills.

After that, we'll teach you about how to use **Chrome's Developer Tools** to debug your code. Debugging skills are
arguably the most important part of being an engineer.

This unit will also look at a **JavaScript function called timers**. This is a function that allows you to call a second
function after a set amount of time elapsed. For instance, if you wanted to create a pop-up to collect the emails of
visitors to your web page, a timer would be an easy way to schedule that.

### Goals

- Review and expand on the web development fundamentals you'll need to succeed in any full-stack career
- Learn how to use Chrome's native debugger to find and fix problems in your code
- Learn about how timers work in JavaScript

## Web Fundamentals Refresher {collapsible="true" default-state="expanded"}

### Web Review

In this subunit, we'll be reviewing the fundamentals of web development to give you good base knowledge to
build upon.

Every page on the internet uses HTML for its content, text, and images, CSS for visual styling, and JavaScript for
interactive elements. Before we move further in this course, it is important you know how to use these languages. They
are present everywhere in our online life. Every type of aspiring programmer must understand how these languages work
and interact.

#### Subunit Goals

- Review essential topics in HTML and CSS
- Review essential topics in JavaScript

### HTML Must Know

- you should be familiar with the following **HTML** elements

#### Essential HTML elements

```html

<div></div>
<h1></h1>
->
<h6></h6>
<p></p>
<span></span>
```

You should be able to explain block elements vs inline elements

#### HTML list elements

```html

<ul></ul>
<ol></ol>
<li></li>
```

What is the difference between an `ul` and an `ol` tag?

- Know these additional HTML elements:

```html

<script></script>
<link rel="" type="" href=""/>
<a href=""></a>
<img src="" alt=""/>
```

- what is the `script` tag used for?
- what is the difference between a `link` tag and an `a` tag?
- why is it important to include an `alt` attribute inside an `img` tag?

- understand the main elements of an HTML table:

```html

<table>
    <thead>
    <tr>
        <th></th>
        <th></th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td></td>
        <td></td>
    </tr>
    </tbody>
</table>
```

#### HTML forms

```html

<form>
    <label for=""></label>
    <input type="text" name="" value="" placeholder=""/>
    <input type="submit" name="" value="Submit"/>
</form>
```

- understand how to connect a label to an input tag using the `for` attribute
- understand the most common input tag attributes
    - type
    - name
    - placeholder
    - value

### CSS Must Know

#### CSS specificity

- what is the specificity of our selectors important?
- in the following code, what color will the background of the `h1` tag be?

```html
<!DOCTYPE html>
<html>
<link rel="stylesheet" href="main.css"/>
<body>
<div>
    <h1 id="id-style" class="class-style"></h1>
</div>
</body>
</html>
```

```css
h1 {
  background: crimson;
}

.class-style {
  background: violet;
}

#id-style {
  background: dodgerblue;
}
```

#### CSS selectors

- know when to use a class selector and when to use id selector
- what is wrong with the following code?

```html
<!DOCTYPE html>
<html>
<link rel="stylesheet" href="main.css"/>
<body>
<div>
    <h1 id="id-style">Hi</h1>
    <h1 id="id-style">There</h1>
</div>
</body>
</html>
```

```css
h1 {
  background: crimson;
}

.class-style {
  background: violet;
}

#id-style {
  background: dodgerblue;
}
```

#### CSS properties

- you should be comfortable controlling the space between html elements
- understand the difference between padding and margin

```css
div {
  width: 10%;
  height: 20%;
  margin: 10px;
  padding: 20px;
}
```

- understand how to control the amount of margin and padding:
    - top
    - right
    - bottom
    - left

```css
div {
  margin-top: 10px;
  margin-right: 12px;
  margin-bottom: 10px;
  margin-left: 8px;
}
```

#### CSS shorthand properties

- be able to apply shorthand properties to the following property types:
    - margin
    - padding
    - border

```css
div {
  margin: 10px 12px 10px 8px;
}
div {
  margin: 20px;
}
div {
  border: 2px solid grey;
}
```

#### CSS positioning

- Understand how to position elements using the following property types:
    - static
    - fixed
    - relative
    - absolute

### JavaScript Must Know

#### Declaring variables

You do not have to know all the details of var, let, and const. However, you should be familiar with these concepts:

| Keyword | Can Reassign | Can Redeclare | Scope Rules |
|---------|--------------|---------------|-------------|
| var     | yes          | yes           | function    |
| let     | yes          | no            | block       |
| const   | no           | no            | block       |

We will be using let and const primarily. You'll dive into the difference later in the course.

#### Conditional logic

- you should understand the differences between:
    - `if`
    - `else if`
    - `else`

You should understand 'js expressions' are always converted to a boolean value when passed to a control statement

```javascript
if(<js expression>){
  // do something
} else if(<js expression>){
    // do something else
    } else {
    // do something else
} else {

}
```

You should be able to explain the difference between the following two snippets of code

```javascript
let n = 10;

if (n > 0) {
  console.log('n is valid');
} else if (n < 100) {
  console.log('n is valid');
} else {
  console.log('n is not valid');
}
```

```javascript
let n = 10;

if (n > 0) {
  console.log('n is valid');
}

if (n < 100) {
  console.log('n is valid');
} else {
  console.log('n is not valid');
}
```

#### Logical operators

- You should have an understanding of the logical operators:
    - || (OR)
    - && (AND)
    - ! (NOT)

#### Primitive data types

- You should be familiar with the following five primitive data types:
    - Numbers
    - Strings
    - Booleans
    - Undefined
    - Null

#### Numbers

- You should be comfortable with:
    - converting a number to a string
    - generating a random number
    - Rounding a number with the following functions:
        - Math.round()
        - Math.ceil()
        - Math.floor()

#### Strings

- You should be comfortable with:
    - Creating a string
    - Converting a string to a number
    - Iterating through each element in a string
    - Making a copy of a string

#### Booleans

- You should know the difference between a 'truthy' and 'falsy' value
- Know the following six 'falsy' values in JavaScript
    - undefined`
    - 0
    - ""
    - false
    - null
    - NaN
- Know two approaches for converting an expression to 'truthy' or 'falsy'
    - `Boolean(<expression>)`
    - `!!<expression>`

#### Iteration

- You should be very comfortable with the syntax for iterating through a string or an array using a 'for loop'

```javascript
for (let i = 0; i < array.length; i++) {
  console.log(array[i]);
}
```

- You should understand the syntax for iterating through a string or an array using a 'while loop'

```javascript
let i = 0;

while (i < array.length) {
  console.log(array[i]);
}
```

- You should understand the difference between a 'for...of' and 'for...in' loop

```javascript
let arr = ['a', 'b', 'c', 'd'];

for (let n of arr) {
  // what will n be?
  console.log(n);
}
```

```javascript
let arr = ['a', 'b', 'c', 'd'];

for (let n in arr) {
  // what will n be?
  console.log(n);
}
```

- You should be comfortable writing a nested for loop
- For example, how would you print each element in the following array of subarrays?

```javascript
let matrix = [
  ['a', 'b', 'c'],
  ['d', 'e', 'f'],
  ['g', 'h', 'i'],
];

for (let i = 0; i < matrix.length; i++) {
  let subArr = matrix[i];
  for (let j = 0; j < subArr.length; j++) {
    console.log(subArr[j]);
  }
}
```

#### Arrays

- You should be comfortable with:
    - creating an array
    - getting and setting elements in an array
    - iterating through arrays
    - making copies of arrays

#### Objects

- You should be comfortable with:

    - creating objects
    - getting and setting key value pairs
    - iterating through objects
    - making copies of objects

- You should know the difference between dot and bracket notation
- You should understand the subtle differences between the following code samples:

```javascript
let arg = 'hi';
let obj = {};

obj.arg = 'there';

    =>{arg: 'there'}
```

```javascript
let arg = 'hi';
let obj = {};

obj[arg] = 'there';

    =>{hi: 'there'}
```

- dot notation uses literal arg string as a key
- bracket notation allows you to pass arguments dynamically

#### Arrays and objects

- you should understand what the following code will do and why:

```javascript
// will this return true or false

[] === [];
```

- Here we are comparing if the array is the same actual array not the values held in the array
- The same result happens when comparing objects

#### Functions

- you should know the syntax for creating functions with and without parameters
- understand how to return values from a function
- how to invoke functions with and without arguments
- function scope vs global scope
- placing functions on objects (methods)

<seealso>
[![MDN Web Docs](https://img.shields.io/badge/MDN_Web_Docs-black?style=flat&logo=mdnwebdocs&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) |
[![W3 Schools](https://img.shields.io/badge/W3Schools-6DA55F?style=flat&logo=w3c&logoColor=white)](https://www.w3schools.com/js/default.asp)
</seealso>
