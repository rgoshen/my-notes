# APIs

## Abbreviations {collapsible="true"}

- \*[API]: Application Programming Interface
- \*[CORS]: Cross-Origin resource Policy
- \*[HTML]: Hypertext Markup Language
- \*[HTTP]: Hypertext Transfer Protocol
- \*[JS]: JavaScript
- \*[JSON]: JavaScript Object Notation
- \*[URL]: Uniform Resource Locator

## Introduction {collapsible="true" default-state="expanded"}

In this subunit, we'll cover the all-important concept of **APIs**. You might have heard the term API before; they're
simpler to work with than they are to explain. Essentially, APIs are a way for you to access data that a company or
website has made publicly available. In the coming resources, you'll learn a bit more about what an API is, the
different kinds of APIs, and how you can fetch and send data to APIs using AJAX. We'll also explore some challenges of
working with APIs.

### Goals

- Define what an API is
- Compare and contrast different kinds of APIs
- Understand the limitations
- Use Terminal and GUI clients for making HTTP requests

## APIs {collapsible="true" default-state="expanded"}

### What is an API?

A set of clearly defined methods of communication between various components.

An API may be for a web-based system, operating system, database system, computer hardware, or software library.

### APIs You Have Used

- [![MDN Web Docs](https://img.shields.io/badge/MDN_Web_Docs-black?style=flat&logo=mdnwebdocs&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/API)

- [![jQuery](https://img.shields.io/badge/jquery-%230769AD.svg?style=flat&logo=jquery&logoColor=white)](https://api.jquery.com/)

- [![Bootstrap](https://img.shields.io/badge/bootstrap-%23563D7C.svg?style=flat&logo=bootstrap&logoColor=white)](https://getbootstrap.com/docs/5.1/utilities/api/)

### Third Party APIs

Companies will provide access to their data (sometimes not for free)

- [![Twitter](https://img.shields.io/badge/Twitter-%231DA1F2.svg?style=flat&logo=Twitter&logoColor=white)](https://developer.twitter.com/en/docs/twitter-api)
- [![Facebook](https://img.shields.io/badge/Facebook-%231877F2.svg?style=flat&logo=Facebook&logoColor=white)](https://developers.facebook.com/docs/)
- [Weather](https://openweathermap.org/api)
- [![Reddit](https://img.shields.io/badge/Reddit-%23FF4500.svg?style=flat&logo=Reddit&logoColor=white)](https://www.reddit.com/dev/api/)
- [![Google Nearby](https://img.shields.io/badge/-Google%20Nearby-%234285F4?style=flat&logo=googlenearby)](https://developers.google.com/maps/documentation/places/web-service/overview)
- [![yelp](https://img.shields.io/badge/Yelp-%23D32323?style=flat&logo=yelp)](https://www.yelp.com/developers)

## Data Formats {collapsible="true" default-state="expanded"}

- When we browse on the web, we make HTTP requests and get HTML back.
- APIs don’t respond with HTML.
    - HTML contains info about page structure. APIs respond with data, not structure.
- They use different data formats like XML and JSON.
    - These are still text-based formats—remember, HTTP is text-based!

### XML

Syntactically similar to HTML, but does not describe presentation like HTML, and many of the tags are custom.

```xml

<person>
    <name>Elie</name>
    <favoriteColor>purple</favoriteColor>
    <city>San Francisco</city>
</person>
```

### JSON

JSON stands for **JavaScript Object Notation**.

JSON looks similar to JS objects, but all the keys must be “double-quoted.”

```json
{
  "person": {
    "name": "Elie",
    "favoriteColor": "purple",
    "city": "San Francisco",
    "favoriteNumber": -97,
    "interests": [
      "CEOing",
      "eating Mediterranean food"
    ],
    "futureDreams": null
  }
}
```

A JSON payload must be sent as a string over HTTP requests.

To convert a JavaScript object to JSON string:

```javascript
JSON.stringify(myObject); // "...string of JSON..."
```

To convert JSON string to JavaScript object:

```javascript
JSON.parse(jsonString); // {prop: value, ...}
```

Most libraries do this for you.

### JSON vs XML

We’ll primarily use JSON: it’s easier to parse & works great with JavaScript!

JSON is also the contemporary standard for most RESTful APIs.

## API Security {collapsible="true" default-state="expanded"}

### AJAX & Same Origin Policy

Many APIs can be used with AJAX

Some cannot unless the JS app is from the “same origin”

This is to prevent subtle security issues.

### Same Origin Policy

- Critical security mechanism that restricts how a document or script loaded from one origin can interact with a
  resource from another origin.
- It helps to isolate potentially malicious documents, reducing possible attacks
- It is **very** restrictive

What constitutes a “different” origin?

- Different domain
- Different protocol
- Different port

### CORS

You can’t use AJAX if the API requires the same origin But the backend

API server can opt in using “CORS”

## Curl {collapsible="true" default-state="expanded"}

**curl** is used in command lines or scripts to transfer data.

Open source & comes with OSX—so it’s easy to use right out of the box

### Making a request using Curl

We do it in the Terminal!

Simplest & most common request/operation made using HTTP is to GET a URL:

```bash
curl http://curl.haxx.se
```

This will return the entire HTML document that the URL holds.

```bash
curl https://api.github.com/users/elie
```

This will return a JSON response from the GitHub API

### Flags with Curl

- `-d` or `--data` to send information to a server

  `-d '{"username":"xyz", "password":"xyz"}'`

- `-X` or `--request` to specify HTTP verb (`-X POST`)
- `-H` or `--header` to specify additional headers

`-H "Content-Type: application/json"`

Example of a larger request

```bash
curl --header "Content-Type: application/json" \
  --request POST \
  --data '{"username":"xyz","password":"xyz"}' \
  https://myapplication.com/login
```

### When to use Curl

- When you are making a simple HTTP(S) request
- When you don’t have any other option
- When you’re doing scripting
- You will also see it in almost all API documentation for examples

## Insomnia {collapsible="true" default-state="expanded"}

A GUI for making HTTP requests.

[![insomnia](https://img.shields.io/badge/-Insomnia-4000BF?style=flat&logo=Insomnia)](https://insomnia.rest/) |
[![insomnia](https://img.shields.io/badge/Docs-Insomnia-4000BF?style=flat&logo=Insomnia)](https://docs.insomnia.rest/)

### Insomnia vs Curl

- You can save previous HTTP requests
- It’s easier to write complex HTTP requests with many headers/long data fields

### Practicing with Insomnia

If you want extra practice, check out [JSONPlaceHolder](https://jsonplaceholder.typicode.com/)
