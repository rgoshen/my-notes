# Introduction to Jest Testing

![jest](Jest.jpg)

## Introduction {collapsible="true" default-state="expanded"}

Testing is one of those things that people either love or hate. Usually testing is something that is hated, until you
work on a project with good tests, and you realize how amazing they are. In this tutorial I am going to show you how to
get started with testing in JavaScript using Jest. I will talk about the code you need in order to write tests, as well
as show you some pitfalls of testing. At the end of the video I will break down the importance of testing and some best
practices you can adhere to in order to make your tests incredible.

## How to Install Jest {collapsible="true" default-state="expanded"}

1. make project folder and cd into it

```bash
mkdir example
cd example
```

1. initialize npm

    1. this will set up the initial project structure and create package.json

```bash
npm init -y
```

1. install [jest](https://jestjs.io/) as a development package

```bash
npm i jest --save-dev
```

**NOTE:** saved as a development dependency only because only used during development

1. change the test script inside the `package.json()` file and replace existing test script with `"jest"`

```json
{
  "scripts": {
    "test": "jest"
  }
}
```

## Why Testing is Important {collapsible="true" default-state="expanded"}

- **Be confident that your code works**. You make a bunch of changes, when you test your code, and it still passes those
  test, then you are more confident in your code. But what happens when you don't test, and then you deploy your code.
  It becomes unstable and your users start to complain that it is not doing what they need it to do.
- **Make better architectural decisions**. It will help you structure your code better and achieve proper separation of
  concerns. You won't be tempted to assign multiple responsibilities to single code blocks as those would be a nightmare
  to unit-test.
- **Pinpoint functionality before coding**. What should happen in case a parameter is null? What if its value is outside
  the expected range or contains too many characters? Do you throw an exception or return null? Unit tests will help you
  discover all these cases. Look at the questions again, and you'll find it's exactly what defines your unit test cases.
  reference [freecodecamp.org](https://www.freecodecamp.org/news/how-to-start-unit-testing-javascript/)

## How to Write Unit Tests in Jest {collapsible="true" default-state="expanded"}

1. create a file and name it the same as the file you want to test i.e.:

```bash
touch fileName.test.js
```

---

```Javascript
function sum(a, b) {
  return a + b;
}

module.exports = sum;
```

{collapsible="true" collapsed-title="sum.js"}

---

```Javascript
const sum = require('./sum');

test('properly add two numbers', () => {
  expect(sum(1, 2)).toBe(3);
});
```

{collapsible="true" collapsed-title="sum.test.js"}

---

```Javascript
function subtract(a, b) {
  return a - b;
}

module.exports = subtract;
```

{collapsible="true" collapsed-title="subtract.js"}

---

---

```Javascript
onst subtract = require('./subtract');

test('properly subtracting two numbers', () => {
  expect(subtract(1, 2)).toBe(-1);
});
```

{collapsible="true" collapsed-title="subtract.test.js"}

---

```Javascript
function cloneArray(arr) {
  return [...arr];
}

module.exports = cloneArray;
```

{collapsible="true" collapsed-title="cloneArray.js"}

---

```Javascript
const { expect } = require('@jest/globals');
const cloneArray = require('./cloneArray');

test('properly clone array', () => {
  const array = [1, 2, 3];

  //   expect(cloneArray(array)).toEqual([1, 2, 3]);
  expect(cloneArray(array)).toEqual(array);
  expect(cloneArray(array)).not.toBe(array); // tests to make sure to separate arrays
});
```

{collapsible="true" collapsed-title="cloneArray.test.js"}

<procedure title="How to write a test" collapsible="true">
    <step>Step 1. Import file you want to test</step>
    <step>Step 2. Set up your describe block</step>
    <step>Step 3. Run the test</step>
    <code-block lang="javascript">test('describe what you are testing', callback)</code-block>
    <p>— First argument passed in actually will get displayed inside the console when you run the test</p>
    <p>— Second parameter is the callback function that actually runs the test</p>
    <p>— Inside the callback you use the expect function that is the actual test - `expect()` returns an expectation object</p>
    <p>— `.toBe()` is the matcher that is called on the returned expectation object - the correct value you expect to be returned by the function you are invoking inside the expect function is passed into the matcher</p>
    <p>— When <a href="https://jestjs.io/">jest</a> runs, it keeps track of all the matchers that fail and prints out nice error messages for you—for a complete list of <a href="https://jestjs.io/">jest matchers</a></p>
</procedure>

## The Importance of Test Coverage {collapsible="true" default-state="expanded"}

- it's good to cover as much code as possible with tests
- will tell you how big a portion of your code is covered by unit tests

<seealso>
[![Jest](https://img.shields.io/badge/Docs-jest-%23C21325?style=flat&logo=jest&logoColor=white)](https://jestjs.io/docs/getting-started) |
[![Youtube](https://img.shields.io/badge/Youtube-FF0000?style=flat&logo=Youtube&logoColor=white)](https://www.youtube.com/watch?v=FgnxcUQ5vho&list=PLZlA0Gpn_vH_63f0HH-dUtkininO7GO6f) |
[![Jest](https://img.shields.io/badge/Docs-jest-%23C21325?style=flat&logo=jest&logoColor=white)](https://jestjs.io/docs/getting-started)
</seealso>
