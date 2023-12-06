# Clean Code

**incomplete**

## Section 1—Getting Started {collapsible="true" default-state="expanded"}

### What is clean code?

Is this clean code?

```py
max = create('Max', 31)
```

Looks like a function that creates a user with an age and return that user object into a variable.

Here is the full code:

_dirty-code-1.py_

```py
def create(m, n):
  if m == 'Max':
    return lambda v: v < n
  elif m == 'Min':
    return lambda v: v > n

max = create('Max', 31)

print(max(15))
print(max(32))
```

So, as it turns out, this does not create a user at all.

It's a function that creates other functions, so it's a factory function or a higher-order function, and these other
functions which are being created, turn out to be validation functions.

We pre-configured them with a certain value, for example, 31. And then we get a function, which we can call thereafter
to compare another value against that created value.

And we either check for that value being smaller or bigger, depending on whether we chose max or min as a parameter for
creating our validation function.

Because there's one thing which clean code certainly is not. It's not code that just works.

The example I showed you will work but it's still not clean code because clean code is not about whether code works or
not. Instead, it's about whether code is easy to read and understand.

It turns out that as a developer, we spend quite a lot of time reading code, understanding code, for example, because we
have to go back to code we wrote in the past to fix a bug or add a feature,or because maybe we need to dive into some
code written by a colleague or by some other developer.

So we need to read a lot of code and therefore, reading code and understanding code should be easy because if it's hard,
we lose a lot of time and productivity.

And ultimately, entire code bases can die because no one's able to fully understand the code.

So for example, here's the same example from before now slightly rewritten.

_clean-code-1.py_

```Python
def create_validator(mode, number):
  if mode == 'Max':
    return lambda value: value < number
  elif mode == 'Min':
    return lambda value: value > number

is_below_max = create_validator('Max', 31)

print(is_below_max(15))
print(is_below_max(32))
```

To be precise, I basically only chose different names.

And now automatically, it becomes cleaner, it becomes easier to read and understand.

It won't take you as long to understand what's going on here as it did before.

And we could, of course, also refactor this in other ways.

We could, for example, also consider creating a class with good names and with all the validation logic baked into the
class.

Something like this.

_clean-code-1.py_

```Python
class ValidateNumber:
  def __init__(self, number):
    self.number = number;

  def is_bigger_than(self, other_number):
    return other_number < self.number

  def is_smaller_than(self, other_number):
    return other_number > self.number

input_number = ValidateNumber(31)

print(input_number.is_bigger_than(15))
print(input_number.is_bigger_than(32))
```

And of course, just to make this clear right away, there will not be a single right way of writing clean code.

Instead, this is one possible solution.

Using a factory function with better names would have been another solution.

Ultimately, it's code which is readable and understandable:

- code which is readable and meaningful
- reduces the cognitive load you have to go through to understand what is written
- should be concise and to the point
- avoid unintuitive names, complex nesting or big code blocks
- follow common best practices and patterns
- should be fun to write and to maintain

### Key Pain Points

1. Naming
    - variables
    - functions
    - classes
2. Structure and comments
    - code formatting
    - good & bad comments
3. Functions
    - length
    - parameters
4. Conditionals & error handling
    - deep nesting
    - missing error handling
5. Classes & data structures
    - missing distinction
    - bloated classes

![clean_code_pain_points.jpg](clean_code_pain_points.jpg)

## Section 2 - Naming - Assigning Names to Variables, Functions, Classes & More {collapsible="true" default-state="expanded"}

- Naming things can sometimes seem like an art form in programming because there are so many different ways

### Why Good Names Matter

- Names should be meaningful

_bad-code.js_

```Javascript
const us = new MainEntity();
us.process();

if (login) {
  // ....
}
```

In this example, `MainEntity` doesn't tell me anything about its purpose nor does "us" mean a person who logs into our
system.

It's not clear from just these two lines of code how they relate to each other without additional context.

On the flip side:
_good-code.js_

```Javascript
const user = new User();
user.save();

if (isLoggedIn) {
  // ...
}
```

Here we have more descriptive names that make it easier for someone else reading or maintaining your codebase later on

Well named "Things" allows the readers to **<span style="color:orange;">understand your code without going through it in
detail</span>**

![why names matter](why-names-matter.png)

#### We will not always agree

`const admin = new Admin();` This is readable
`const admin = new AdminUser();` So is this

### Choosing Good Names

#### How to Name Things Correctly

| Variables & Constants                                        | Functions/Methods                                      | Classes                                       |
|--------------------------------------------------------------|--------------------------------------------------------|-----------------------------------------------|
| Data containers                                              | Commands or calculated values                          | Use classes to create "things"                |
| e.g. user input data, validation results, a list of products | e.g. nd data to a server, check if user input is valid | e.g. a user, a product, a http request        |
| Use **nouns** or short phrases with **adjectives**           | Use **verbs** or short phrases with **adjectives**     | Use **nouns** or short phrases with **nouns** |
| `const userData = {...}` or `const isValid = ...`            | `sendData()` or `inputIsValid()`                       | `class User{...}` or `class RequestBody{...}` |

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
