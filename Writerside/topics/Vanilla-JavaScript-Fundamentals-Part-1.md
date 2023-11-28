# Vanilla JavaScript Fundamentals Part 1

![javascript](javaScript.jpeg)

## Abbreviations {collapsible="true"}

- \*[CSS]: Cascading Style Sheet
- \*[HTML]: Hypertext Markup Language
- \*[JS]: JavaScript

Let’s dive right in to JavaScript!

## Learning Outcomes {collapsible="true" default-state="expanded"}

- How do you declare a variable?
- What are three different ways to declare a variable?
- Which one should you use when?
- What are the rules for naming variables?
- What are operators, operands, and operations?
- What is concatenation and what happens when you add numbers and strings together?
- What are the different types of operators in JavaScript?
- What is the difference between `==` and `===`?
- What are operator precedence values?
- What are the increment/decrement operators?
- What is the difference between prefixing and post-fixing them?
- What are assignment operators?
- What is the “Unary +” Operator?

## How to Run JavaScript Code {collapsible="true" default-state="expanded"}

All JavaScript we will be writing in the majority of the Foundations course will be run via the browser. Later lessons
in Foundations and the NodeJS path will show you how to run JavaScript outside of the browser environment. Outside of
these lessons, for now you should always default to running your JavaScript in the browser unless otherwise specified,
otherwise you may run into unexpected errors.

The simplest way to get started is to simply create an HTML file with the JavaScript code inside of it. Type the basic
HTML skeleton into a file on your computer somewhere:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Page Title</title>
    <meta charset="UTF-8"/>
</head>
<body>
<script>
    // Your JavaScript goes here!
    console.log('Hello, World!');
</script>
</body>
</html>
```

Save and open this file up in a web browser (you can use Live Server to do this!) and then open up the browser’s console
by right-clicking on the blank webpage and selecting “Inspect” or “Inspect Element”. In the ‘Developer Tools’ pane find
and select the ‘Console’ tab, where you should see the output of our **<span style="color:red">console.log</span>**
statement.

> `console.log()` is the command to print something to the developer console in your browser.
> You can use this to print the results from any of the following articles and exercises to the console.
> We encourage you to code along with all the examples in this and future lessons.

Another way to include JavaScript in a webpage is through an external script. This is very similar to linking external
CSS docs to your website.

```html

<script src="javascript.js"></script>
```

JavaScript files have the extension `.js` similar to `.css` for stylesheets. External JavaScript files are used for more
complex scripts.

## Variables {collapsible="true" default-state="expanded"}

You can think of variables as simply “storage containers” for data in your code. Until recently there was only one way
to create a variable in JavaScript — the <span style="color:red">var</span> statement. But in the newest JavaScript
versions we have two more ways — <span style="color:red">let</span> and <span style="color:red">const</span>.

1. This [variable tutorial](https://javascript.info/variables) will explain to you everything you need to know! Be sure
   to do the Tasks at the end. Information won’t stick without practice!

The above tutorial mentioned this, but it’s important enough to note again: <span style="color:red">let</span>
and <span style="color:red">const</span> are both relatively new ways to declare variables in JavaScript. In _many_
tutorials (and code) across the internet you’re likely to encounter <span style="color:red">var</span> statements. Don’t
let it bother you! There’s nothing inherently wrong with <span style="color:red">var</span>, and in most
cases <span style="color:red">var</span> and <span style="color:red">let</span> behave the same way. But sometimes the
behavior of <span style="color:red">var</span> is _not_ what you would expect. Just stick to <span style="color:red">
let</span> (and <span style="color:red">const</span>) for now. The precise differences between <span style="color:red">
var</span> and <span style="color:red">let</span> will be explained later.

A variable is a "named storage" for data. The statement below creates (in other words, _declares_) a variable witt the
name "message":

```javascript
let message;
```

Now we can put some data into it by using the assignment operator `=`:

```javascript
let message;
message = 'Hello';
```

The string is now saved into the memory area associated with the variable. We can access it using the variable name:

```javascript
let message;
message = 'Hello!';

alert(message); // shows the variable content
```

To be more concise, we can combine the variable declaration and assignment into a single line:

```javascript
let message = 'Hello!';

alert(message); // Hello!
```

We can also declare multiple variables in one line:

```javascript
let user = 'John',
  age = 25,
  message = 'Hello!';
```

The above is not recommended though due to harder readability, best to keep each declaration to its own line

```javascript
let user = 'John';
let age = 25;
let message = 'Hello!';
```

A variable should be declared only once. A repeated declaration of the same variable is an error:

```javascript
let message = 'This';

// repeated 'let' leads to an error
let message = 'That'; // SyntaxError: 'message' has already been declared
```

### Variable naming

There are two limitations on variable names in JavaScript:

1. The name must contain only letters, digits, or the symbols '$' and '\_'.
1. The first character must not be a digit.

Examples of valid names:

1. `let userName;`
1. `let test123;`

When the name contains multiple words, **<span style="color:blue">camelCase</span>** is commonly used. Ex:
myVeryLongName

The dollar sign '$' and the underscore '\_' can also be used in names.

> **Note: Case matters**
>
> Variable named 'apple' and 'AppLE' are two completely different variables.

> **Non-Latin letters are allowed but not recommended**
>
> It is possible to use any language, including cyrillic letters and eve hieroglyphs, like this:

```javascript
let имя = '...';
let 我 = '...';
```

Technically, there is no error here. Such names are allowed, but there is an international convention to use English in
variable names. Even if we’re writing a small script, it may have a long life ahead. People from other countries may
need to read it some time.

> **⁉ Reserved names**
>
> There is
>
a [list of reserved words](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#keywords),
> which cannot be used as variable names because they are used by the language itself.

### Name Things Right

Talking about variables, there’s one more extremely important thing.

A variable name should have a clean, obvious meaning, describing the data that it stores.

Variable naming is one of the most important and complex skills in programming. A quick glance at variable names can
reveal which code was written by a beginner versus an experienced developer.

Please spend time thinking about the right name for a variable before declaring it. Doing so will repay you handsomely.

Some good-to-follow rules are:

- Use human-readable names like **userName** or **shoppingCart**.
- Stay away from abbreviations or short names like **a**, **b**, **c**, unless you really know what you’re doing.
- Make names maximally descriptive and concise. Examples of bad names are **data** and **value**. Such names say
  nothing. It’s only okay to use them if the context of the code makes it exceptionally obvious which data or value the
  variable is referencing.
- Agree on terms within your team and in your own mind. If a site visitor is called a “user” then we should name related
  variables **currentUser** or **newUser** instead of **currentVisitor** or **newManInTown**.

> **Reuse or create?**
>
> And the last note.
> There are some lazy programmers who, instead of declaring new variables, tend to reuse existing ones.
>
> As a result, their variables are like boxes into which people throw different things without changing their stickers.
> What’s inside the box now?
> Who knows?
> We need to come closer and check.
>
> Such programmers save a little on variable declaration but lose ten times more on debugging.
>
> An extra variable is good, not evil.
>
> Modern JavaScript minifiers and browsers optimize code well enough, so it won’t create performance issues.
> Using different variables for different values can even help the engine optimize your code.

## Numbers {collapsible="true" default-state="expanded"}

Numbers are the building blocks of programming logic! In fact, it’s hard to think of any useful programming task that
doesn’t involve at least a little basic math… so knowing how numbers work is obviously quite important. Luckily, it’s
also fairly straightforward.

1. This [W3Schools lesson](https://www.w3schools.com/js/js_arithmetic.asp) followed
   by [this one](https://www.w3schools.com/js/js_numbers.asp), are good introductions to what you can accomplish with
   numbers in JavaScript.
1. This [MDN article](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Math) covers the same info
   from a slightly different point of view, while also teaching you how to apply some basic math in JavaScript. There’s
   much more that you can do with numbers, but this is all you need at the moment.
1. Read through (and code along with!) this [article](https://javascript.info/operators) about operators in Javascript.
   Don’t forget to do the “Tasks” at the bottom of the page! It will give you a pretty good idea of what you can
   accomplish with numbers (among other things!) in JavaScript.

### Terms: "unary", "binary", "operand"

operand
: is what operators are applied to

- For instance, in the multiplication of 5 \* 2 there are two operands: the left operand is 5 and the right operand is
    2. Sometimes, people call these “arguments” instead of “operands”.

unary
: it has a single operand

- the unary negation `-` reverses the sign of a number

```javascript
let x = 1;
x = -x;

alert(x); // -1, unary negation was applied
```

binary
: it has to operands

- The same minus exists in binary form as well:

```javascript
let x = 1,
  y = 3;
alert(y - x); // 2, binary minus subtracts values
```

### String concatenation with binary +

Let’s meet features of JavaScript operators that are beyond school arithmetics.

Usually, the plus operator `+` sums numbers.

But, if the binary `+` is applied to strings, it merges (concatenates) them:

```javascript
let s = 'my' + 'string';
alert(s); // mystring
```

Note that if any of the operands is a string, then the other one is converted to a string too.

For example:

```javascript
alert('1' + 2); // "12"
alert(2 + '1'); // "21"
```

See, it doesn’t matter whether the first operand is a string or the second one.

Here's a more complex example:

```javascript
alert(2 + 2 + '1'); // "41" and not "221"
```

Here, operators work one after another. The first `+` sums two numbers, so it returns 4, then the next `+` adds the
string 1 to it, so it’s like `4 + '1' = '41'`.

```javascript
alert('1' + 2 + 2); // "122" and not "14"
```

Here, the first operand is a string, the compiler treats the other two operands as strings too. The 2 gets concatenated
to '1', so it’s like `'1' + 2 = "12"` and `"12" + 2 = "122"`.

The binary `+` is the only operator that supports strings in such a way. Other arithmetic operators work only with
numbers and always convert their operands to numbers.

Here’s the demo for subtraction and division:

```javascript
alert(6 - '2'); // 4, converts '2' to a number
alert('6' / '2'); // 3, converts both operands to numbers
```

### Numeric conversion, unary +

The plus `+` exists in two forms: the binary form that we used above and the unary form.

The unary plus or, in other words, the plus operator `+` applied to a single value, doesn’t do anything to numbers. But
if the operand is not a number, the unary plus converts it into a number.

For example:

```javascript
// No effect on numbers
let x = 1;
alert(+x); // 1

let y = -2;
alert(+y); // -2

// Converts non-numbers
alert(+true); // 1
alert(+''); // 0
```

It actually does the same thing as `Number(...)`, but is shorter.

The need to convert strings to numbers arises very often. For example, if we are getting values from HTML form fields,
they are usually strings. What if we want to sum them?

The binary plus would add them as strings:

```javascript
let apples = '2';
let oranges = '3';

alert(apples + oranges); // "23", the binary plus concatenates strings
```

If we want to treat them as numbers, we need to convert and then sum them:

```javascript
let apples = '2';
let oranges = '3';

// both values converted to numbers before the binary plus
alert(+apples + +oranges); // 5

// the longer variant
// alert( Number(apples) + Number(oranges) ); // 5
```

From a mathematician’s standpoint, the abundance of pluses may seem strange. But from a programmer’s standpoint, there’s
nothing special: unary pluses are applied first, they convert strings to numbers, and then the binary plus sums them up.

Why are unary pluses applied to values before the binary ones? As we’re going to see, that’s because of their _higher_
precedence.

### Assignment

Let’s note that an assignment `=` is also an operator. It is listed in the precedence table with the very low priority
of 2.

That’s why, when we assign a variable, like `x = 2 * 2 + 1`, the calculations are done first and then the `=` is
evaluated, storing the result in `x`.

```javascript
let x = 2 * 2 + 1;

alert(x); // 5
```

#### Assignment = returns a value

The fact of `=` being an operator, not a “magical” language construct has an interesting implication.

All operators in JavaScript return a value. That’s obvious for `+` and `-`, but also true for `=`.

The call `x = value` writes the `value` into `x` and then returns it.

Here’s a demo that uses an assignment as part of a more complex expression:

```javascript
let a = 1;
let b = 2;

let c = 3 - (a = b + 1);

alert(a); // 3
alert(c); // 0
```

In the example above, the result of expression `(a = b + 1)` is the value which was assigned to `a` (that is `3`). It is
then used for further evaluations.

Funny code, isn’t it? We should understand how it works, because sometimes we see it in JavaScript libraries.

Although, please don’t write the code like that. Such tricks definitely don’t make code clearer or readable.

#### Chaining assignments

Another interesting feature is the ability to chain assignments:

```javascript
let a, b, c;

a = b = c = 2 + 2;

alert(a); // 4
alert(b); // 4
alert(c); // 4
```

Chained assignments evaluate from right to left. First, the rightmost expression `2 + 2` is evaluated and then assigned
to the variables on the left: `c`, `b` and `a`. At the end, all the variables share a single value.

Once again, for the purposes of readability it’s better to split such code into few lines:

```javascript
c = 2 + 2;
b = c;
a = c;
```

That’s easier to read, especially when eye-scanning the code fast.

#### Modify-in-place

We often need to apply an operator to a variable and store the new result in that same variable.

For example:

```javascript
let n = 2;
n = n + 5;
n = n * 2;
```

This notation can be shortened using the operators `+=` and `*=`:

```javascript
let n = 2;
n += 5; // now n = 7 (same as n = n + 5)
n *= 2; // now n = 14 (same as n = n * 2)

alert(n); // 14
```

Short “modify-and-assign” operators exist for all arithmetical and bitwise operators: `/=`, `-=`, etc.

Such operators have the same precedence as a normal assignment, so they run after most other calculations:

```javascript
let n = 2;

n *= 3 + 5;

alert(n); // 16  (right part evaluated first, same as n *= 8)
```

### JavaScript Arithmetic Operators

Arithmetic operators perform arithmetic on numbers (literals or variables).

| Operator | Description          |
|----------|----------------------|
| +        | Addition             |
| -        | Subtraction          |
| \*       | Multiplication       |
| \*\*     | Exponential (ES2016) |
| /        | Division             |
| %        | Modulus (Remainder)  |
| ++       | Increment            |
| --       | Decrement            |

### Arithmetic Operations

A typical arithmetic operation operates on two numbers.

The two numbers can be literals:

```javascript
let x = 100 + 50;
```

or variables:

```javascript
let x = a + b;
```

or expressions:

```javascript
let x = (100 + 50) * a;
```

### Operators and Operands

The numbers (in an arithmetic operation) are called **operands**.

The operation (to be performed between the two operands) is defined by an **operator**.

| Operand | Operator | Operand |
|---------|----------|---------|
| 100     | +        | 50      |

### Adding

The **addition** operator (+) adds numbers:

```javascript
let x = 5;
let y = 2;
let z = x + y;
```

### Subtracting

The **subtraction** operator (-) subtracts numbers:

```javascript
let x = 5;
let y = 2;
let z = x - y;
```

### Multiplying

The **multiplication** operator (\*) multiplies numbers:

```javascript
let x = 5;
let y = 2;
let z = x * y;
```

### Dividing

The division operator (/) divides numbers:

```javascript
let x = 5;
let y = 2;
let z = x / y;
```

### Remainder

The **modulus** operator (%) returns the division remainder:

```javascript
let x = 5;
let y = 2;
let z = x % y;
```

> In arithmetic, the division of two integers produces a **quotient** and a **remainder**.
>
> In mathematics, the result of a **modulo operation** is the **remainder** of an arithmetic division.

### Incrementing/Decrementing

Increasing or decreasing a number by one is among the most common numerical operations.

So, there are special operators for it:

The **increment** operator (++) increments a variable by 1:

```javascript
let counter = 2;
counter++; // works the same as counter = counter + 1, but is shorter
alert(counter); // 3
```

The **decrement** operator (--) decrements a variable by 1:

```javascript
let counter = 2;
counter--; // works the same as counter = counter - 1, but is shorter
alert(counter); // 1
```

> **⁉ Important**
>
> Increment/decrement can only be applied to variables.
> Trying to use it on a value like `5++` will give an error.

The operators `++` and `-` can be placed either before or after a variable.

- When the operator goes after the variable, it is in “postfix form”: `counter++`.
- The “prefix form” is when the operator goes before the variable: `++counter`.

Both of these statements do the same thing: increase `counter` by `1`.

Is there any difference? Yes, but we can only see it if we use the returned value of `++/--`.

Let’s clarify. As we know, all operators return a value. Increment/decrement is no exception. The prefix form returns
the new value while the postfix form returns the old value (prior to increment/decrement).

To see the difference, here’s an example:

```javascript
let counter = 1;
let a = ++counter; // (*)

alert(a); // 2
```

In the line `(*)`, the prefix form `++counter` increments `counter` and returns the new value, `2`. So, the `alert`
shows `2`.

Now, let’s use the postfix form:

```javascript
let counter = 1;
let a = counter++; // (*) changed ++counter to counter++

alert(a); // 1
```

In the line `(*)`, the postfix form `counter++` also increments `counter` but returns the old value (prior to
increment). So, the `alert` shows `1`.

> **ℹ Increment/decrement among other operators**
>
> The operators ++/-- can be used inside expressions as well.
> Their precedence is higher than most other arithmetical operations.
> For instance:
>
> `let counter = 1;`
>
> `alert( 2 * ++counter ); // 4`
>
> Compare with:
>
> `let counter = 1;`
>
> `alert( 2 * counter++ ); // 2, because counter++ returns the "old" value`
>
> Though technically okay, such notation usually makes code less readable.
> One line does multiple things – not good.
>
> While reading code, a fast “vertical” eye-scan can easily miss something like `counter++` and it won’t be obvious that
> the variable increased.
>
> We advise a style of “one line – one action”:
>
> `let counter = 1;`
>
> `alert( 2 * counter );`
>
> `counter++;`

### Bitwise Operators

Bitwise operators treat arguments as 32-bit integer numbers and work on the level of their binary representation.

These operators are not JavaScript-specific. They are supported in most programming languages.

The list of operators:

- AND ( & )
- OR ( | )
- XOR ( ^ )
- NOT ( ~ )
- LEFT SHIFT ( << )
- RIGHT SHIFT ( >> )
- ZERO-FILL RIGHT SHIFT ( >>> )

These operators are used very rarely, when we need to fiddle with numbers on the very lowest (bitwise) level. We won’t
need these operators any time soon, as web development has little use of them, but in some special areas, such as
cryptography, they are useful. You can read the Bitwise Operators chapter on MDN when a need arises.

### Comma

The comma operator `,` is one of the rarest and most unusual operators. Sometimes, it’s used to write shorter code, so
we need to know it in order to understand what’s going on.

The comma operator allows us to evaluate several expressions, dividing them with a comma `,`. Each of them is evaluated
but only the result of the last one is returned.

For example:

```javascript
let a = (1 + 2, 3 + 4);

alert(a); // 7 (the result of 3 + 4)
```

Here, the first expression `1 + 2` is evaluated and its result is thrown away. Then, `3 + 4` is evaluated and returned
as the result.

> **ℹ Comma has a very low precedence**
>
> Please note that the comma operator has very low precedence, lower than `=,` so parentheses are important in the
> example above.
>
> Without them: `a = 1 + 2, 3 + 4` evaluates `+` first, summing the numbers into `a = 3, 7`, then the assignment
> operator `=` assigns `a = 3`, and the rest is ignored. It’s like `(a = 1 + 2), 3 + 4`.

Why do we need an operator that throws away everything except the last expression?

Sometimes, people use it in more complex constructs to put several actions in one line.

For example:

```javascript
// three operations in one line
for (a = 1, b = 3, c = a * b; a < 10; a++) {
 ...
}
```

Such tricks are used in many JavaScript frameworks. That’s why we’re mentioning them. But usually they don’t improve
code readability so we should think well before using them.

### Exponentiation

The **exponentiation** operator (\*\*) raises the first operand to the power of the second operand:

```javascript
let x = 5;
let z = x ** 2; // result is 25
```

x \*\* y produces the same result as `Math.pow(x,y)`:

```javascript
let x = 5;
let z = Math.pow(x, 2); // result is 25
```

### Operator Precedence

Operator precedence describes the order in which operations are performed in an arithmetic expression.

```javascript
let x = 100 + 50 * 3;
```

Is the result of example above the same as 150 \* 3, or is it the same as 100 + 150?

Is the addition or the multiplication done first?

As in traditional school mathematics, the multiplication is done first.

Multiplication (\*) and division (/) have higher **precedence** than addition (+) and subtraction (-).

And (as in school mathematics) the precedence can be changed by using parentheses:

```javascript
let x = 100 + 50 * 3;
```

When using parentheses, the operations inside the parentheses are computed first.

When many operations have the same precedence (like addition and subtraction), they are computed from left to right:

```javascript
let x = 100 + 50 - 3;
```

### JavaScript Operator Precedence Values

| Value | Operator   | Description                  | Example              | Associativity |
|-------|------------|------------------------------|----------------------|---------------|
| 19    | ()         | Express grouping             | (3 + 4)              | n/a           |
|       |            |                              |                      |
| 18    | .          | Member                       | person.name          | left-to-right |
| 18    | []         | Member                       | person["name"]       | left-to-right |
| 18    | ()         | Function call                | myFunction()         | left-to-right |
| 18    | ?.         | Optional Chaining (ES2020)   | obj.val?.prop        | n/a           |
| 18    | new        | new (with argument list)     | new ... (...)        | n/a           |
|       |            |                              |                      |
| 17    | new        | new (without argument list)  | new Date()           | right-to-left |
|       |            |                              |                      |
| 16    | ++         | Postfix Increment            | i++                  | n/a           |
| 16    | --         | Postfix Decrement            | i--                  | n/a           |
|       |            |                              |                      |
| 15    | ++         | Prefix Increment             | ++i                  | right-to-left |
| 15    | --         | Prefix Decrement             | --i                  | right-to-left |
| 15    | !          | Logical NOT                  | !(x==y)              | right-to-left |
| 15    | ~          | Bitwise NOT                  | ~(x==y)              | right-to-left |
| 15    | typeof     | Type                         | typeof x             | right-to-left |
| 15    | +          | Unary plus                   | +"10"                | right-to-left |
| 15    | -          | Unary negation               | -10                  | right-to-left |
| 15    | void       |                              | void (2 == '2')      | right-to-left |
| 15    | delete     |                              | delete Employee.name | right-to-left |
| 15    | await      |                              | await expression     | right-to-left |
|       |            |                              |                      |
| 14    | \*\*       | Exponentiation (ES2016)      | 10\*\*2              | right-to-left |
|       |            |                              |                      |
| 13    | \*         | Multiplication               | 10\*5                | left-to-right |
| 13    | /          | Division                     | 10/5                 | left-to-right |
| 13    | %          | Division Remainder           | 10 % 5               | left-to-right |
|       |            |                              |                      |
| 12    | +          | Addition                     | 10+5                 | left-to-right |
| 12    | -          | Subtraction                  | 10-5                 | left-to-right |
|       |            |                              |                      |
| 11    | <<         | Bitwise Shift left           | x<<2                 | left-to-right |
| 11    | \>>        | Bitwise Shift right          | x>>2                 | left-to-right |
| 11    | \>>>       | Bitwise Shift right unsigned | x>>>2                | left-to-right |
|       |            |                              |                      |
| 10    | <          | Less than                    | x < y                | left-to-right |
| 10    | <=         | Less than or equal           | x <= y               | left-to-right |
| 10    | \>         | Greater than                 | x > y                | left-to-right |
| 10    | \>=        | Greater than or equal        | x >= y               | left-to-right |
| 10    | in         | Property in Object (ES2016)  | "PI" in Math         | left-to-right |
| 10    | instanceof | Instance of Object (ES2016)  | instanceof Array     | left-to-right |
|       |            |                              |                      |
| 9     | ==         | Equal                        | x == y               | left-to-right |
| 9     | ===        | Strict Equal                 | x === y              | left-to-right |
| 9     | !=         | Unequal                      | x != y               | left-to-right |
| 9     | !==        | Strict Unequal               | x !== y              | left-to-right |
|       |            |                              |                      |
| 8     | &          | Bitwise AND                  | x & y                | left-to-right |
|       |            |                              |                      |               |
| 7     | ^          | Bitwise XOR                  | x ^ y                | left-to-right |
|       |            |                              |                      |               |
| 6     | \          |                              | Bitwise OR           | x \           | y               | left-to-right |
|       |            |                              |                      |               |
| 5     | &&         | Logical AND                  | x && y               | left-to-right |
|       |            |                              |                      |               |
| 4     | \          | \                            |                      | Logical OR    | x \|\| y             | left-to-right |
| 4     | ??         | Nullish Coalescing           | x ?? y               | left-to-right |
|       |            |                              |                      |               |
| 3     | ?:         | Condition (ternary)          | ? "Yes" : "No"       | right-to-left |
|       |            |                              |                      |
| 2     | =          | Assignment                   | x=y                  | right-to-left |
| 2     | +=         | Assignment                   | x+=y                 | right-to-left |
| 2     | /=         | Assignment                   | x/=y                 | right-to-left |
| 2     | -=         | Assignment                   | x-=y                 | right-to-left |
| 2     | \*=        | Assignment                   | x\*=y                | right-to-left |
| 2     | %=         | Assignment                   | x%=y                 | right-to-left |
| 2     | <<=        | Assignment                   | x<<=y                | right-to-left |
| 2     | \>>=       | Assignment                   | x>>=y                | right-to-left |
| 2     | \>>>=      | Assignment                   | x>>>=y               | right-to-left |
| 2     | &=         | Assignment                   | x&=y                 | right-to-left |
| 2     | ^=         | Assignment                   | x ^= y               | right-to-left |
| 2     | \          | =                            | Assignment           | x \           |= y              | right-to-left |
| 2     | yield      | Pause Function (ES2016)      | yield x              | right-to-left |
|       |            |                              |                      |
| 1     | ,          | Comma                        | 5, 6                 | left-to-right |

<seealso>
[![MDN Web Docs](https://img.shields.io/badge/MDN_Web_Docs-black?style=flat&logo=mdnwebdocs&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/JavaScript) |
[![W3 Schools](https://img.shields.io/badge/W3Schools-6DA55F?style=flat&logo=w3c&logoColor=white)](https://www.w3schools.com/js/default.asp) |
[The Odin Project](https://www.theodinproject.com/)
</seealso>
