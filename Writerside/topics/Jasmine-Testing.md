# Jasmine Testing

![jasmine](jasmine-white-horizontal.png)

## Abbreviations {collapsible="true"}

- \*[CSS]: Cascading Style Sheet
- \*[HTML]: Hypertext Markup Language

## Introduction {collapsible="true" default-state="expanded"}

In this subunit, you'll learn a foundation skill for software development: **writing tests**.

Every time you write a new function or method, you'll need to test it to make sure it works. Otherwise, there could be
major problems down the line, and it will take hours to find and fix them. Why not avoid that by writing a simple **unit
test** to ensure each chunk of code functions like it's supposed to?

You'll be testing code every day on the job, and testing is the #1 skill that employers are looking for in junior
developers. This subunit will introduce you to one of the most popular JavaScript testing libraries: **Jasmine**. You'll
learn how to write unit tests for your functions and how to visualize the tests you're running.

### Goals

- Explain what testing is
- Understand why we write tests
- Write tests with [Jasmine](https://jasmine.github.io/)

## Writing Tests {collapsible="true" default-state="expanded"}

- writing code to test your code

### Why test

- Manual testing is boring and error-prone
    - So we tend to not re-run things that “work”
    - And therefore don’t notice when they break
    - small programs we can manually check all pieces of functionality before pushing our code
    - as the program becomes larger, it becomes impossible to catch everything that might break
- Tests often clarify expectations of a function
    - What should legal input/output be?
- Tests are often a great way to understand what code does
- It’s a core skill for professional developers

### Testing Tools

- [Jasmine](https://jasmine.github.io/)
    - javascript
- [Jest](https://jestjs.io/)
    - commonly used with [node.js](https://nodejs.org/en/) & [react.js](https://reactjs.org/)
    - provides multiple layers on top of [Jasmine](https://jasmine.github.io/)

### Jasmine

- [Jasmine](https://jasmine.github.io/) is a popular JavaScript testing framework
- We’ll use [Jasmine](https://jasmine.github.io/) for testing until we get to Python
- We’ll see another framework, [Jest](https://jestjs.io/), with Node and React

### Running Tests in the Browser with Jasmine

```html
<!DOCTYPE html>
<html>
<head>
    <title>Taxes Tests</title>
    <!-- include CSS for Jasmine -->
    <link
            rel="stylesheet"
            href="https://unpkg.com/jasmine-core/lib/jasmine-core/jasmine.css"
    />
</head>
<body>
<!-- include JS for Jasmine -->
<script src="https://unpkg.com/jasmine-core/lib/jasmine-core/jasmine.js"></script>
<script src="https://unpkg.com/jasmine-core/lib/jasmine-core/jasmine-html.js"></script>
<script src="https://unpkg.com/jasmine-core/lib/jasmine-core/boot.js"></script>
</body>
</html>
```

Then open this HTML page in browser

### Testing Process

- testing allows us to automate the tedious work of making sure new lines of code don't break pre-existing code
- in order to work with [Jasmine](https://jasmine.github.io/) in the browser, we need to import the library using a
  script tag

### Writing tests with Jasmine

#### Jasmine Setup

- Files to include
    - 1 CSS file
    - 2 JavaScript files
    - ensure the JavaScript files are located just before the closing body tag but before all other JavaScript files

**Best Practice**: use separate files for tests vs code (taxes.js vs taxes.test.js)

Write your functions that will be tested:

_demo/taxes.js_

```javascript
function calculateTaxes(income) {
  if (income > 30000) {
    return income * 0.25;
  } else {
    return income * 0.15;
  }
}
console.log(calculateTaxes(500));
```

Write a test file:

_demo/taxes.test.js_

```javascript
it('should calculate lower-bracket taxes', function () {
  expect(calculateTaxes(10000)).toEqual(1500);
  expect(calculateTaxes(20000)).toEqual(3000);
});
it('should calculate higher-bracket taxes', function () {
  expect(calculateTaxes(50000)).toEqual(12500);
  expect(calculateTaxes(80000)).toEqual(20000);
});
```

Let’s break that down

```javascript
it('should calculate lower-bracket taxes', function () {
  expect(calculateTaxes(10000)).toEqual(1500);
  expect(calculateTaxes(20000)).toEqual(3000);
});
it('should calculate higher-bracket taxes', function () {
  expect(calculateTaxes(50000)).toEqual(12500);
  expect(calculateTaxes(80000)).toEqual(20000);
});
```

- Test cases are functions passed to `it(...)`
    - The first argument becomes test case name (shown by Jasmine)
        - helps to id which test failed
    - The second argument is a callback function that executes the test

_demo/taxes.test.js_

```javascript
it('should calculate lower-bracket taxes', function () {
  expect(calculateTaxes(10000)).toEqual(1500);
  expect(calculateTaxes(20000)).toEqual(3000);
});
it('should calculate higher-bracket taxes', function () {
  expect(calculateTaxes(50000)).toEqual(12500);
  expect(calculateTaxes(80000)).toEqual(20000);
});
```

- Test cases can contain any normal code plus “expectations”
    - we pass the function we want to test as the argument to the `except()`
        - When we call `calculateTaxes()`, we are invoking the actual function
        - Typically, it is a function we pass, but it can be any JavaScript we want to test
- Format is `expect(someValue).someMatcher(...)`

### Matchers

- `.toEqual(obj)` - Has the same value (e.g., different lists with same values match)
- `.toBe(obj)` - Is the same object (e.g., different lists with same items don’t)
- `.toContain(obj)` - Does object/array contain this item?
- `.not.` - Add before matcher to invert (e.g. `expect(...).not.toEqual(7)`)

For complete documentation on [matchers](https://jasmine.github.io/api/edge/matchers.html)

### What to test

- Test every function in at least one way
- Think about “edges”
    - What if the list were empty?
    - What about non-integer numbers?
    - What if the file can’t be found?
    - Is the first case/last case handled differently?

### Testable Code

Write code that is easier to test!

- More functions & smaller functions: easier to test (& debug!)
- Don’t mix logic & UI in a function

_first version_

```javascript
function playTicTacToe() { // ...
let winner = checkForWinner(); }
function checkForWinner() {
// code for checking board here... if (winner) {
    alert(winner + " wins!");
  }
return winner;
}
```

_refactored with testing in mind_

```javascript
function playTicTacToe() {
  // ...
  let winner = checkForWinner();
  if (winner) {
    announceWinner(winner);
  }
}
function checkForWinner() {
  // code for checking board here...
  return winner;
}
function announceWinner(winner) {
  alert(winner + ' wins!');
}
```

<seealso>
[![Jasmine](https://img.shields.io/badge/-Jasmine-%238A4182?style=flat&logo=Jasmine&logoColor=white)](https://jasmine.github.io/)
</seealso>
