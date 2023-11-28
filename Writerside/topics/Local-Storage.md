# Local Storage

![javascript](javaScript.jpeg)

## Abbreviations {collapsible="true"}

- \*[API]: Application Programming Interface
- \*[DOM]: Document Object Model
- \*[JS]: JavaScript
- \*[JSON]: JavaScript Object Notation

## Introduction {collapsible="true" default-state="expanded"}

In this subunit, we'll explore **`localstorage`** and see how this is used to persist information across tabs and pages.
Storing information in the browser is extremely common when building web applications and one of the easiest ways to do
that with JavaScript is through **`localstorage`**.

### Goals

- Utilize `localstorage` to save information in the browser
- Compare adn contrast `localstorage` and `sessionstorage`
- Add and remove primitives to/from `localstorage`
- Add and remove objects to/from `localstorage`

## localstorage {collapsible="true" default-state="expanded"}

### What is localstorage

`localstorage` is a mechanism for storing information in the browser for a specific domain

The API is quite easy to use and very minimal - so let's get started with it!

## localstorage vs sessionstorage {collapsible="true" default-state="expanded"}

When you read more about localstorage you will also hear about something called `sessionstorage`

- data stored in `localstorage` has no expiration time
- data stored in `sessionstorage` gets cleared when the browsing session ends

## Modifying localstorage {collapsible="true" default-state="expanded"}

The most important thing to remember is that all of your keys in `localstorage` or `sessionstorage` must be **strings**.

`localstorage` stores everything as strings, so it’s just good to get in the habit of setting your keys as strings to
avoid confusion.

### Setting an item in localstorage

We do this using the [setItem](https://developer.mozilla.org/en-US/docs/Web/API/Storage/setItem) method

```javascript
localstorage.setItem('firstName', 'Colt');
localstorage.setItem('favoriteNumber', 33);
localstorage.setItem('hasChickens', true);
```

### Retrieving an item in localstorage

To retrieve we use the [getItem](https://developer.mozilla.org/en-US/docs/Web/API/Storage/getItem) method (only passing
in the key)

```javascript
localstorage.getItem('firstName'); // "Colt"
```

You can alternatively just access items on the localstorage object:

```javascript
localstorage.firstName; // "Colt"
```

If you refresh the page - you should be able to still retrieve these keys in localstorage!

### Clearing localstorage

To delete a key we use the [removeitem](https://developer.mozilla.org/en-US/docs/Web/API/Storage/removeItem) function

```javascript
localstorage.removeItem('firstName');
```

To clear everything from localstorage we use the clear function

```javascript
localstorage.clear();
```

## Adding Objects to localstorage {collapsible="true" default-state="expanded"}

So far we have only added primitives, which is nice and easy, but what happens when we start adding objects?

Well, things get a bit trickier.... Let's see what happens:

```javascript
const friends = ['Lana', 'Hayden', 'Jessie'];

localstorage.setItem('friends', friends);
localstorage.getItem('friends');
```

When we get the friends key from localstorage, we don't have an array anymore - we have a string!

Remember, when dealing with localstorage, everything gets converted into a string

In order to get back our original data type, we need to convert this array to a special string format called JSON

JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It
is easy for machines to parse and generate

We will be discussing it quite a bit more later on

## Working with JSON in the browser {collapsible="true" default-state="expanded"}

JavaScript has a built-in JSON object, and on this object are two methods used to convert JavaScript data into JSON, and
to parse JSON strings into JavaScript

- `JSON.stringify` - is used to convert JavaScript to JSON (or stringify)
- `JSON.parse` parses a string as JSON

Using these two methods allows us to preserve the intended data structure when it is something other than a string:

```javascript
const friends = ['Lana', 'Hayden', 'Jessie'];

// the JSON.stringify function
// converts the friends array into a JSON string

localstorage.setItem('friends', JSON.stringify(friends));

// JSON.parse converts the JSON string
// back into JavaScript (in this case, a valid array)

JSON.parse(localstorage.getItem('friends'));
```

<seealso>
[![MDN Web Docs](https://img.shields.io/badge/MDN_Web_Docs-black?style=flat&logo=mdnwebdocs&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) |
[![W3 Schools](https://img.shields.io/badge/W3Schools-6DA55F?style=flat&logo=w3c&logoColor=white)](https://www.w3schools.com/js/default.asp)
</seealso>
