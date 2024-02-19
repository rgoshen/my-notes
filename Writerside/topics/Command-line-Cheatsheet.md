# Command-line Cheatsheet

## General command syntax

| command | option(s) | arguments(s)      |
|---------|-----------|-------------------|
| ls      | -lh       | /usr/bin          |
| sort    | -u        | users.txt         |
| grep    | -i        | "needle" haystack |

- command: action you want to take
- option(s): tell the command how to operate
- argument(s): tell the command what it will operate on

## Text navigation shortcuts {collapsible="true" default-state="expanded"}

- ctrl + a (^a) - move to beginning of line
- ctrl + e (^e) - move to end of line
- ctrl + ⬅ (left arrow) - move left one word
- ctrl + ➡ (right arrow) - move right one word
- ctrl + u (^u) - remove/crop from cursor to start
- ctrl + k (^k) - remove/crop from cursor to end
- ctrl + y (^y) - paste cropped text
- ctrl + shift + v - paste from clipboard
- ctrl + shift + c - copy to clipboard
- ⬆ (up arrow) - recall previous commands
- ⬇ (down arrow) - scroll previous commands
- ctrl + r - search command history

## Finding help for commands {collapsible="true" default-state="expanded"}

manual : man

`man <command>`

- if you know the name of the command but want to know what options/flags you can use

Example:

```Bash
man ls
```

`apropos`

- if you don't know the name of the command

Example:

```bash
apropos "list"
```

## Commands at the shell prompt {collapsible="true" default-state="expanded"}

- increase font size: `ctrl+shift+ (+)`
- decrease font size: `ctrl+shift+ (-)`

> does not work in WSL

{style="warning"}

## Misc keyboard shortcuts {collapsible="true" default-state="expanded"}

Tab completion

- automatically completes a file or folder name

Example:

`ls -l De` + tab completes Desktop
`ls -l Do` + tab will show possible options

> does not work in WSL

{style="warning"}

- cancel: `ctrl+c`
- clear: `clear`

<seealso>
    <!--Provide links to related how-to guides, overviews, and tutorials.-->
</seealso>