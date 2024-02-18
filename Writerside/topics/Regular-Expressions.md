# Regular Expressions

## Test Method {collapsible="true" default-state="expanded"}

- `.test()` - takes regular expression (regex), applies it to a string (which is placed inside the parenthesis) &
  returns
  true or false depending if the pattern is found or not

Example:

```Javascript
let testStr = "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr); // true
```

## Multiple Patterns {collapsible="true" default-state="expanded"}

- use `alternation` or `OR` operator: `|` (pipe)
    - matches pattern before and after it

Example:

`/yes | no/`

## Ignore Case {collapsible="true" default-state="expanded"}

- use "i" flag

Example:

`/ignore case/i`

- will match this pattern regardless if any is capitalized or not

## Extract Matches {collapsible="true" default-state="expanded"}

- `.match()` - extract the actual match
    - apply the method on a string and pass in the regex pattern inside the parenthesis

Example:

```Javascript
'Hello, World!'.match(/Hello/); // ["Hello"]
let testStr = 'Regular expressions';
let testRegex = /expressions/;
testStr.match(testRegex); // ["expressions"]
```

## Find more than the first match {collapsible="true" default-state="expanded"}

- use "g" flag

Example:

```Javascript
let testStr = "Repeat, Repeat, Repeat";
let testRegex  = /Repeat/g;
testStr.match(testRegex); // ["Repeat", "Repeat", "Repeat"]
```

## Match anything with wildcard period {collapsible="true" default-state="expanded"}

- the wildcard "." will match any **one** character

Example:

```Javascript
let testStr = "I'll hum a song";
let testRegex = /hu./;
testRegex.test(testStr); // true
```

## Match single character with multiple possibilities {collapsible="true" default-state="expanded"}

- search for a literal pattern with character classes
- character classes allow you to define a group of characters
    - place them inside `[]`

Example:

- want to match beg, bug, big but not bog

Regex: `/b[eiu]g/`

## Match everything but letters and numbers {collapsible="true" default-state="expanded"}

- include letters and numbers: `/[A-Za-z0-9]/`
- equivalent to `\w`: `/\w/`

- exclude letters and numbers: `/[^A-Za-z0-9]/`
- equivalent to `\W`: `/\W/`

Example:

```Javascript
let shorthand = /\W/;
let numbers = '42%';
let sentence = 'Coding!';
numbers.match(shorthand); // ["%"]
sentence.match(shorthand); // ["!"]
```

- useful for when you want to search ahead for multiple patterns
    - positive look ahead: (?=...)
    - negative look ahead: (?!...)
- `?`: possible existence of previous character if exact number

## Match all numbers {collapsible="true" default-state="expanded"}

character class: `/[0-9]/` or shorthand `\d`: `/\d/`

## Match all non-numbers {collapsible="true" default-state="expanded"}

character class: `/[^0-9]/` or shorthand `\D`: `/\D/`

## Restrict possible user names {collapsible="true" default-state="expanded"}

1. can only use alpha-numeric characters
2. can not begin with numbers and must only be at the end ( can ne zero or more at the end only)
3. letters can by upper or lower case
4. use name must be at least two characters long and if only two characters, must be alpha characters only (no numbers)

Examples:

s1: `/^[a-z][a-z]+\d*\S|^[a-z]\d\d+\S/i`

s2: `/^[a-z]([0-9]{2,}|[a-z+\d*)\S]/i`

- `{2,}`: ends with two or more numbers
- `{3, 5}`: between 3 and 5 times
- `{}`: quantity specifiers
- `+`: 1 or more characters
- `*`: 0 or more characters
- `\S`: non-white spaces
- character class: `[^/r/t/f/n/v]`

## Match whitespace {collapsible="true" default-state="expanded"}

- s = space
- r = carriage return
- t = tab
- f = form feed
- n = new line
- v = vertical tab

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
