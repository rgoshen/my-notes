# How to Implement Linked Lists with Test Driven Development

**incomplete?**

## Introduction {collapsible="true" default-state="expanded"}

Linked lists are one of the most popular data structures interviewers ask about in technical interviews. You will
probably never have to implement one in a real day-to-day job, but knowing how to write a linked list and understanding
how they work is crucial to passing a technical interview.

On top of covering linked lists in this tutorial, I will also be covering how you can use test driven development to
make writing code easier. We will be designing the entirety of the linked list with test-driven development (TDD) to
show you how to write better tests.

## How to do test driven development {collapsible="true" default-state="expanded"}

1. **Create precise tests:** Developers need to create precise unit tests to verify the functionality of specific
   features. They must ensure that the test compiles so that it can execute. In most cases, the test is bound to fail.
   This is a meaningful failure as developers are creating compact tests based on their assumptions of how the feature
   will behave.
2. **Correcting the Code:** Once a test fails, developers need to make the minimal changes required to correct the code
   so that it can run successfully when re-executed.
3. **Refactor the Code:** Once the test runs successfully, check for redundancy or any possible code optimizations to
   enhance overall performance. Ensure that refactoring does not affect the external behavior of the program.

The image below represents a high-level TDD approach towards development:

![tdd_high_level](tdd_high_level_flow_chart.png)

Image taken from [Browserstack.com](https://www.browserstack.com/guide/what-is-test-driven-development)

## What a linked list is? {collapsible="true" default-state="expanded"}

- alternative to an array data structure
- both are linear data structure
- an array is list of objects with each object accessed by an index starting at 0 and going to n-elements and contains a
  finite number of elements that is defined at creation
- a linked list on the other hand does not have indexes for its stored elements, it stores an object similar to an
  array,
  however, instead of a consecutive index numbers, the node (element) has a reference to the next node in the list
- linked list is basically a group of nodes where each node points to the next node by means of a pointer
    - node is composed of data and a reference to the next node
- start off with a head node (first or 0 element), it has its value and the reference to next element only
- tail node is the very last node, it stores data and reference points to null
- each node after the head node will also have its value and a reference to next node and so on
- eventually it ends with the tail node where it also has its value but does not have any reference to a next node
- three type of linked lists
    - singly linked list—each node references the next node except for the tail node which ends the list
    - doubly linked list—each node references the next node and its previous node except for the head node which
      starts the list
    - circular linked list—this is similar to a singly linked list except the tail node references back to the head
      node

![linked-lists](types-of-linked-list.png)
image from [faceprep.in](https://www.faceprep.in/data-structures/linked-list-introduction/)

#### Why use a linked list instead of an array?

- one advantage of linked lists is that elements can be added to it indefinitely without reallocation or reorganization
  of the entire structure because that data items need not be stored contiguously in memory. An array on the other hand
  will eventually get filled or have to be resized for making an insertion whenever needed (a costly operation that
  isn't always possible)
- elements are also be easily removed from linked lists whereas removing elements from an array leaves empty spaces that
  are a waste of computer memory or performing a shift operation in arrays increases the cost thus makes it expensive
- linked lists are more efficient with adding and removing elements than arrays
    - add an element at the beginning: array you can do this but you have to move existing first element down a position
      which in turn every other element also must move down (O(n) time because who have to loop through all existing
      elements) whereas in a linked list you can simply create the node, give it a reference to the existing head node
      and now the new node becomes the head node (O(1) time)
    - now if you are not operating on the first element of a linked list then it becomes O(n) time because you have to
      start with the first node and traverse through the list to the node you want conversely much quicker to get random
      elements in an array because you pass in the index of the element you want

#### Operations of Linked Lists

- **Insertion**—inserts an element at specified positions in the list
- **Deletion**—deletes an element at specified positions in the list
- **Search**—searches an element using the given value
- **Update**—update an element at specified position with the given value

## How to create a linked list {collapsible="true" default-state="expanded"}

1. make project folder and cd into it

```bash
mkdir example
cd example
```

2. initialize npm

    1. this will set up the initial project structure and create package.json

```bash
npm init -y
```

3. install [jest](https://jestjs.io/) as a development package

```bash
npm i jest --save-dev
```

4. Create _linkedList.js_

<procedure title="Create linkedList.js" collapsible="true">
    <step>Step 1. create a `LinkedList` class and export it so the automated tests can access it</step>
    <step>Step 2. create an `constructor();` method with no parameters because we want to create an empty linked list by default</step>
    <step>Step 3. inside the constructor method create two references</step>
    <step>Step 3a.`this.head = null;`—beginning or first node of a linked list</step>
    <step>Step 3b.`this.length = ;.` - time saver so we can keep track of the length and not have to loop through it every time to determine the length </step>
    <step>Step 4. create another class `LinkedListNode` for the node itself or just create a normal js object `linkedListNode ={value: null, next: null};` **note:** for consistency better to go with option 1</step>
    <step>Step 5. create a `constructor(value, next);` in the node class</step>
    <step>Step 6. create `insertAtHead(data)` method in the linked list class</step>
    <step>Step 7. inside the `insertAtHead()` method create a newNode</step>
    <step>Step 7a. pass in data and `this.head` since this is going in front of the head</step>
    <step>Step 8. then set head to `newNode` and 1 to length</step>
    <step>Step 9. perform first manual test in `app.js`</step>
</procedure>

```Javascript
class LinkedList {
  constructor() {
    this.head = null;
    this.length = 0;
  }

  insertAtHead(data) {
    const newNode = new LinkedListNode(data, this.head);
    this.head = newNode;
    this.length++;
  }

  removeHead() {
    this.head = this.head.next;
    this.length--;
  }

  getByIndex(index) {
    if (index < 0 || index >= this.length) return null;

    let current = this.head;
    for (let i = 0; i < index; i++) {
      current = current.next;
    }
    return current;
  }

  insertAtIndex(index, value) {
    if (index === 0) return this.insertAtHead(value);

    const prev = this.getByIndex(index - 1);
    if (prev === null) return null;

    prev.next = new LinkedListNode(value, prev.next);
    this.length++;
  }

  removeAtIndex(index) {
    if (index === 0) return this.removeHead();

    const prev = this.getByIndex(index - 1);
    if (prev === null) return null;

    prev.next = prev.next.next;
    this.length--;
  }

  print() {
    let output = '';
    let current = this.head;
    while (current) {
      output = `${output}${current.value} -> `;
      current = current.next;
    }
    console.log(`${output}null`);
  }
}

// option 1
class LinkedListNode {
  constructor(value, next) {
    this.value = value;
    this.next = next;
  }
}

// option 2
// let linkedListNode = { value: null, next: null };

// helper function to help with testing getByIndex test
LinkedList.fromValues = function (...values) {
  const ll = new LinkedList();
  for (let i = values.length - 1; i >= 0; i--) {
    ll.insertAtHead(values[i]);
  }
  return ll;
};

module.exports = LinkedList;
```

{collapsible="true" collapsed-title="linkedList.js"}

5. create _linkedList.test.js_ for automated testing and to drive writing the file

<procedure title="Create linkList.test.js" collapsible="true">
<step>Step 1. import LinkedList class `const LinkedList = require('./[LinkedList](/javascript/data_structures/linked_lists_with_TDD/notes/linkedListjs.md)');`</step>
<step>Step 2. write a describe block `describe('#insertAtHead'() => {});`</step>
<step>Step 2a. first parameter is a string of the name of the method/function to be tested - '#' is just a convention to be used when testing a method of a class</step>
<step>Step 2b. second parameter is callback function that contains all the test information we want</step>
<step>Step 3. inside of callback function create first test `test('adds node to beginning of the list', () => {});`</step>
<step>Step 3a. similar to the describe block first parameter is a string saying what the test does and second parameter is another callback function that contains the code to run to test whatever we want to test</step>
<step>Step 4. to run the tests inside the `package.json()` file and replace existing test script with `"jest --coverage"`</step>
</procedure>

```json
{
  "scripts": {
    "test": "jest --coverage"
  }
}
```

6. then run test

```bash
❯ npm run test

> linked_lists_with_tdd@1.0.0 test
> jest --coverage

 PASS  ./linkedList.test.js
  #insertAtHead
    ✓ adds node to the beginning of list (1 ms)

---------------|---------|----------|---------|---------|-------------------
File           | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s
---------------|---------|----------|---------|---------|-------------------
All files      |     100 |      100 |     100 |     100 |
 linkedList.js |     100 |      100 |     100 |     100 |
---------------|---------|----------|---------|---------|-------------------
Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        0.236 s
Ran all test suites.
```

> `npm run test` will run all tests

{style="note"}

> Try to get 100% test coverage if possible but not necessary - 100% test coverage means all lines of code in
> object file were tested

{style="note"}

```Javascript
const { expect } = require('@jest/globals');
const LinkedList = require('./linkedList');

describe('#insertAtHead', () => {
  test('adds node to the beginning of list', () => {
    const ll = new LinkedList();
    ll.insertAtHead(10);
    const oldHead = ll.head;
    ll.insertAtHead(20);

    expect(ll.head.value).toBe(20);
    expect(ll.head.next).toBe(oldHead);
    expect(ll.length).toBe(2);
  });
});

describe('#getByIndex', () => {
  describe('with index less than 0', () => {
    test('it returns null', () => {
      //helper function in linkedList.js
      const ll = LinkedList.fromValues(10, 20);

      expect(ll.getByIndex(-1)).toBeNull();
    });
  });

  describe('with index greater than list length', () => {
    test('it returns null', () => {
      const ll = LinkedList.fromValues(10, 20);

      expect(ll.getByIndex(5)).toBeNull();
    });
  });

  describe('with index 0', () => {
    test('it returns the head', () => {
      const ll = LinkedList.fromValues(10, 20);

      expect(ll.getByIndex(0).value).toBe(10);
    });
  });

  describe('with index in the middle', () => {
    test('it returns the element at that index', () => {
      const ll = LinkedList.fromValues(10, 20, 30, 40);

      expect(ll.getByIndex(2).value).toBe(30);
    });
  });
});

describe('#insertAtIndex', () => {
  describe('with index less than 0', () => {
    test('it does not insert anything', () => {
      const ll = LinkedList.fromValues(10, 20);
      ll.insertAtIndex(-1, 30);

      expect(ll.length).toBe(2);
    });
  });

  describe('with index greater than list length', () => {
    test('it does not insert anything', () => {
      const ll = LinkedList.fromValues(10, 20);
      ll.insertAtIndex(5, 30);

      expect(ll.length).toBe(2);
    });
  });

  describe('with index 0', () => {
    test('insert at the head', () => {
      const ll = LinkedList.fromValues(10, 20);
      ll.insertAtIndex(0, 30);

      expect(ll.head.value).toBe(30);
      expect(ll.head.next.value).toBe(10);
      expect(ll.length).toBe(3);
    });
  });

  describe('with index in the middle', () => {
    test('insert at the given index', () => {
      const ll = LinkedList.fromValues(10, 20, 30, 40);
      ll.insertAtIndex(2, 50);
      const node = ll.getByIndex(2);

      expect(node.value).toBe(50);
      expect(node.next.value).toBe(30);
      expect(ll.length).toBe(5);
    });
  });
});

describe('#removeHead', () => {
  test('removes the head', () => {
    const ll = LinkedList.fromValues(10, 20, 30);
    ll.removeHead();

    expect(ll.head.value).toBe(20);
    expect(ll.length).toBe(2);
  });
});

describe('#removeAtIndex', () => {
  describe('with index less than 0', () => {
    test('it does not remove anything', () => {
      const ll = LinkedList.fromValues(10, 20);
      ll.removeAtIndex(-1);

      expect(ll.length).toBe(2);
    });
  });

  describe('with index greater than list length', () => {
    test('it does not remove anything', () => {
      const ll = LinkedList.fromValues(10, 20);
      ll.removeAtIndex(-1);

      expect(ll.length).toBe(2);
    });
  });

  describe('with index 0', () => {
    test('remove the head', () => {
      const ll = LinkedList.fromValues(10, 20, 30);
      ll.removeAtIndex(0);

      expect(ll.head.value).toBe(20);
      expect(ll.head.next.value).toBe(30);
      expect(ll.length).toBe(2);
    });
  });

  describe('with index in the middle', () => {
    test('remove at the given index', () => {
      const ll = LinkedList.fromValues(10, 20, 30, 40);
      ll.removeAtIndex(2);
      const node = ll.getByIndex(1);

      expect(node.value).toBe(20);
      expect(node.next.value).toBe(40);
      expect(ll.length).toBe(3);
    });
  });
});
```

{collapsed-title="linkedList.test.js" collapsible="true"}

> When writing tests for a class, you do not want to use other methods of that class to test the current method. If
> the other method fails, then all tests for the current method would fail whether the method logic was written
> correctly or not - here is where you would create a helper function see linkedList.js

{style="note"}

7. create `app.js` see we can run code to manually test the `linkedList` file

<procedure title="Create app.js" collapsible="true">
<step>import LinkedList `const LinkedList = require('linkedList.js');`</step>
<step>create a new linked list `const ll = new LinkedList();`</step>
<step>insert value 10 at the head `ll.insertAtTheHead(10);`</step>
<step>insert value 20 at the head `ll.insertAtTheHead(20);`</step>
<step>log 'll' to console `console.log(ll);`</step>
<step>run app.js `node app.js`</step>
<step>go to `linkedList.test.js`</step>
</procedure>

```Javascript
const LinkedList = require('./linkedList');

// const ll = new LinkedList();

// ll.insertAtHead(10);
// console.log(ll);
// ll.insertAtHead(20);
// console.log(ll);

const ll = LinkedList.fromValues(10, 20, 30, 40);
ll.print();
// console.log(ll.getByIndex(0).value);
// ll.insertAtIndex(2, 60);
// ll.removeHead();
ll.removeAtIndex(2);
ll.print();
```

{collapsed-title="app.js" collapsible="true"}

8. go to `linkedList.js` for remaining instructions

From here on out you write tests, test by `npm run test`, tests should fail and then write the method based on your test
cases, run the tests again `npm run test` and now they should pass - keep doing this until you have created all your
methods you need to write.

## How to write proper tests {collapsible="true" default-state="expanded"}

1. go to `linkedList.test.js` on writing tests

<seealso>
- [Web Dev Simplified](https://www.youtube.com/watch?v=gJjPWA8wpQg&list=PLZlA0Gpn_vH_7qOMYNO7fdvIN9_kYEo2I)
- [Jest Docs](https://jestjs.io/docs/getting-started)
- [What is Test Driven Development](https://www.browserstack.com/guide/what-is-test-driven-development)
</seealso>
