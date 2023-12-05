# Terminal

## Intermediate Terminal {collapsible="true" default-state="expanded"}

### Links

#### Links Intro

- file type that exists as pointer, a reference to another file
    - when you alter teh original file, you also alter all of the links
- since we have files and folders located all over the file system, it becomes difficult to identify where many of these
  are located. Fortunately, we can create a link (aka as alias) to a file or folder using the `ln` command.
    - `ln <path-to-link> <name-of-link>`

#### Hard Links

- physical copy that stays sync'd to original unless original deleted
- there are two kinds of links we can make, hard & symbolic links
- hard links are carbon copy of file that is linked
- will automatically update or sync when linked file has any changes made
- duplicate of the original file
    - both are a pro & con
        - pro: stays sync'd
        - con: because takes up as much room in memory as original
    - stays up to date with original
    - if original deleted, the hard linked file persists regardless
    - if move original file, the linked file persists regardless

#### Symbolic Links (Symlinks)

- reference to file
- if original file deleted or moved, the link is broken
- doesn't take up same space in memory as original file
- to create a symbolic link, we use the `-s` flag
    - `ln -s <path-to-link> <name-of-link>`
- creates a pointer back to the original
- delete or move original file the link breaks
- can symlink to a directory, hard links to a directory don't work

### The Find Command

- one fo the most useful terminal commands is the `find` command
- to find a specific file in your current directory, you can simply type find and the name of the file. (If you try to
  find a folder you will find all of the contents inside as well)

`find <exact match of what you are looking for>`

- to find something with a bit more complexity, use the following pattern:

1. find
2. a filepath
3. an expression (this is when you have the most flexibility)

- this is nice if we know exactly the name of the file we are looking for, but many times we need to use wildcard
  characters
- here are some:
    - `*`: any number of characters
    - `?`: one character
    - `[]`: any of the characters inside the brackets

Examples:

- find inside of some folder (assume we are inside that folder) anything that ends with `.html`
    - `find . -name "*.html"`
- find inside of some folder (assume we are inside that folder) anything that ends with a three letter file extension
    - `find . -name "*.???"`
- find inside of some folder (assume we are inside that folder) anything that starts with the letters f, t, or s
    - `find . -name "[fts]*"`

### Grep

#### Grep Intro

- search within files
- stands for Global Regular Expression Print
- `i` flag: case insensitive
- `A` flag: display a certain number of lines after
- `v` flag: invert pattern (you can think of this as anything NOT what you were searching for)
- `c` flag: count the number of matches
- `n` flag: show line number
- `w` flag: characters in a row (word)
- `d` flag: digit (0-9)
- `r` flag: recursive (with out this grep cannot search through a directory)
- `.`: current directory

#### Grep Regex

- Regex (aka Regular Expression) are functions that search for a particular pattern in alphanumeric characters
- Regex is used to define patterns in a string of characters
    - used to search a text for potential matches
- Regex is common and quite powerful
    - use them to check whether a user has submitted a properly formatted email address or phone number
- Wildcards
    - `.`: matches any character
        - Example: how many names have a full name that is four characters long?
            - `grep -wc "..." names.txt`
    - `*`: match zero or more of the preceding character or expression
        - Example: how many names start with a captial 'T'?
            - `grep -wc "T.*" names.txt`
    - `[]`: any specific characters
        - Example: how many names start with a capital 'L', 'M' or 'E'?
            - `grep -wc "[L, M, E].*" names.txt``
    - `[^]`: do not match
        - Example: how many names do not start with a capital 'T'?
            - `grep -wc "[^T].*" name.txt`
    - `\`: escape character
        - Example: get all digits
            - `grep '==\d' requirements.txt`
        - Example: get all that begin with '==' & 1 digit
            - `grep '==\d\.' requirements.txt`

#### Recursive Grep

- find w/in multiple files w/in a directory
    - `grep -ir 'bycrypt' .`

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
