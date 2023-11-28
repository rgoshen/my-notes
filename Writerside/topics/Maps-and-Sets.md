# Maps and Sets

![javascript](javaScript.jpeg)

## Introduction {collapsible="true" default-state="expanded"}

Unlike programming languages like Python and Java, JavaScript comes with only a few built-in Data Structures. ES2015
tackled this issue by adding in two data structures common in other languages: **maps and sets**.

In this subunit, we'll teach you what you need to know to get up and running with these two data structures. You'll
learn what they are, how to use them, and what kinds of problems they are best suited for. At the end of the subunit,
we'll have a few exercises for you to complete.

### Data Structure in JavaScript

- Data structures are formats for efficiently collecting or storing data
- So far we've seen Arrays and Objects
- ES2015 introduces two new ones, Maps and Sets

## Maps {collapsible="true" default-state="expanded"}

- Also called "hash maps" in other languages
- Until ES2015 - objects were replacements for maps
- Similar to objects, except the keys can be ANY data type!
- Created using the new keyword

### What is Looks Like

```javascript
let firstMap = new Map();
firstMap.set(1, ’Ash');
firstMap.set(false, 'a boolean');
firstMap.set('nice', 'a string');
firstMap.delete('nice'); // true
firstMap.size; // 2
```

Keys can be any type!

```javascript
let arrayKey = [];
firstMap.set(arrayKey, [1, 2, 3, 4, 5]);
let objectKey = {};
firstMap.set(objectKey, { a: l });
firstMap.get(1); // 'Ash'
firstMap.get(false); // 'a boolean'
firstMap.get(arrayKey); // [1,2,3,4,5] fi rstMap.get(objectKey); // {a:l}
```

**We** can easily iterate over the map!

```javascript
firstMap.forEach((v) => console.log(v));
// Ash
// a boolean // [1,2,3,4,5] // {a:l}
```

Maps also provide:

- `.keys()` to iterate over all the keys
- `.values()` to iterate over all the values
- `.entries()` to iterate over all the [key,value] pairs
- a Symbol.iterator which means we can use a for...of loop to iterate over the keys, values or both!

Here's what it looks like to access everything in a map with .entriesQ and destructuring!

```javascript
let m = new Map([
  [1, 'Ayisha'],
  [2, 'Shani'],
  [3, 'Michelle'],
]);

for (let [key, value] of m.entries()) {
  console.log(key, value);
}

// 1 "Ayisha"
// 2 "Shani"
// 3 "Michelle"
```

### Why use maps

- Finding the size is easy - no more loops or Object.keys()
- The keys can be any data type!
- You can accidentally overwrite keys on the Object.prototype in an object you make - maps do not have that issue
- Iterating over keys and values in a map is quite easy as well
- If you need to look up keys dynamically (they are not hard coded strings)
- If you need keys that are not strings!
- If you are frequently adding and removing key/value pairs
- Are key-value pairs frequently added or removed?
- If you are operating on multiple keys at a time

## Sets {collapsible="true" default-state="expanded"}

- All values in a set are unique
- Any type of value can exist in a set
- Created using the new keyword
- Exist in quite a few other languages, ES2015 finally brings them to JavaScript

### Creating Sets

- To make a new Set, we call new Set()
- When making a new Set, you can also pass in an iterable object,

```javascript
const hashTags = new Set(['#selfie', '#nofilter']);
```

### Adding to Sets

There is only a single method to add items to a set: **add()**

```javascript
const annoyingHashTags = new Set();
annoyingHashTags.add('#YOLO');
annoyingHashTags.add('#Blessed');
annoyingHashTags.add('#YOLO'); // will not be added!
```

### size

Use the **size** property to determine the number of values stored in a Set:

```javascript
const annoyingHashTags = new Set();
annoyingHashTags.add('#YOLO');
annoyingHashTags.add('#Blessed');
annoyingHashTags.size; //2
```

### Checking for an element in the Set

- Sets do not support random access,
- but we are able to check if a set contains a given value using **has()**

```javascript
const annoyingHashTags = new Set();
annoyingHastTags.add('#YOLO');
annoyingHastTags.add('#Blessed');

annoyingHashTags.has('#YOLO'); // true
annoyingHashTags.has('#Selfie'); // false
```

### Removing values in a set

To remove a single value from a set, use **delete()**

```javascript
const annoyingHashtags = new Set();

annoyingHashTags.add('#YOLO');
annoyingHashTags.add('#Blessed');

annoyingHashTags.has('#YOLO'); // true

annoyingHashTags.delete('#YOLO');

annoyingHashTags.has('#YOLO'); // false
```

**We** can also use **clear()** to empty a set of all values:

```javascript
annoyingHashTags.clear();
```

### Iterating over a set

- Sets are iterable objects, so we can use them with for...of loops or the spread operator
- Values in a set are ordered by insertion order. Here's one example of looping over a Set:

```javascript
const annoyingHashTags = new Set();

annoyingHashTags.add('#YOLO');
annoyingHashTags.add('#Blessed');
annoyingHashTags.add('#NoFilter');

for(let val of annoyingHashTags){
  console.log('Please don't use', val);
}
```

### When you use sets

- Removing duplicate values
- Uniqueness required
- Efficiently checking if an item is in a collection (much better than arrays)

<seealso>
[![MDN Web Docs](https://img.shields.io/badge/MDN_Web_Docs-black?style=flat&logo=mdnwebdocs&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) |
[![W3 Schools](https://img.shields.io/badge/W3Schools-6DA55F?style=flat&logo=w3c&logoColor=white)](https://www.w3schools.com/js/default.asp)
</seealso>
