# VIM Cheatsheet

## Standard commands {collapsible="true" default-state="expanded"}

### Modes

command mode: `:`
normal mode: `esc`
insertion mode: `i`
replacement mode: `r`
visual mode: `v`

quit: `:q`
save: `:w`
quit & save: `:wq`
quit w/o saving: `:q!`

### Insert/append

append (right after the cursor and puts you in insert mode)(**normal mode**): `a`

- `<esc>` to exit back to  **normal mode**
  append at the end of the current line (**normal mode**): `A`
- `<esc>` to exit back to  **normal mode**
  insert (cursor must be before where you want to insert)(**normal mode**): `i`
- this put you in **insert mode**
- `<esc>` to exit back to **normal mode**

### Delete

delete character (cursor must be on the character)(**normal mode**): `x`

delete operator(**normal mode**): `d [number] <motion>`
delete to the end of the line (**normal mode**): `d$`
delete to start of next word (exc its first character)(**normal mode**): `dw`

- delete the next _n_ words: `d2w`
  delete to end of current word (inc its first character)(**normal mode**): `de`
  delete the whole line (**normal mode**): `dd`
- delete the next _n_ lines (**normal mode**): `2dd`

### Motions

move by word (**normal mode**): `w`
move to end of line (**normal mode**): `$`

### Move

move up (**normal mode**): `j`
move down (**normal mode**):  `k`
move left (**normal mode**): `h`
move right (**normal mode**): `l`

move to end of word (**normal mode**): `e`
move to end of the line (**normal mode**): `$`
move to the beginning of the line (**normal mode**): `0`
move to the beginning of a word (**normal mode**): `w`

- move to the beginning of _n_ words (**normal mode**): `2w`
- move to the end of _n_ words (**normal mode**): `3e`

see position in file (**normal mode**): `ctrl + g`
goto beginning of file  (**normal mode**): `G`
goto end of file  (**normal mode**): `gg`
goto to line _n_  (**normal mode**): `103 shift + g`

jump from one window to another (**normal mode**) `ctrl + w`

### Undo

undo the last commands (**normal mode**): `u`
fine a whole line (**normal mode**): `U`
redo the last commands (**normal mode**): `ctrl + r`
put the line below the cursor (**normal mode**): `p`

### Replace

replace the character at the cursor (**normal mode**): `r<character>`
replace more than one character (cursor should be on first character to replace) (**normal mode**) `R<characters>`

### Change

change operator (**normal mode**): `c [number] <motion>`
change from cursor to end of word (**normal mode**): `ce`
change the whole line (**normal mode**): `cc`
change from cursor to end of the line (**normal mode**): `c$`

**NOTE**:  You can use the Backspace key to correct mistakes while typing.

### Search

search command  (**normal mode**): `/`
search for a word  (**normal mode**): `/error`
search for the next occurrence  (**normal mode**): `n`
search for the next occurrence (opposite direction)  (**normal mode**): `N`
search for a phrase in the opposite direction  (**normal mode**): `?phrase`

go back from where you came from  (**normal mode**): `ctrl + o`
go forward  (**normal mode**): `ctrl + i`

find a matching '(', '[', or '{'  (put cursor on one) (**normal mode**): `%`

### Substitute Command

`:s/old/new/g` (move to the line) (**command mode**)
To change every occurrence of a character string between two lines (**command mode**) `:#,#s/old/new/g`  (where #,# are
the line numbers of the range of lines where the substitution is to be done)
change every occurrence in the whole file (**command mode**)`:%s/old/new/g`
find every occurrence in the whole file (**command mode**) `:%s/old/new/gc` (prompt whether to substitute or not)

### Execute External Command

`:! <external command>` (**command mode**)

**NOTE**:  It is possible to execute any external command this way, also with arguments.

**NOTE**:  All  :  commands must be finished by hitting `<ENTER>`
From here on we will not always mention it.

### Selecting Text

`v` (**visual mode**) - then move cursor over lines to select lines over over words to select words

### Retrieving and Merging Files

insert contents of a file (**command mode**) `:r <filename>`

### Open Command

open a line below the cursor and place you in insert mode (**normal mode**) `o`
open a line above the cursor and place you in insert mode (**normal mode**) `O`

### Copy and Paste

copy (**visual mode**) `y`
paste (**normal mode**) `p`

**NOTE**: You can also use 'y' as an operator: `yw` yanks (copies) one word, `yy` yanks the whole line, then `p` puts
that line

### Set Option

set ignore case option (for searches) (**command mode**) `:set ic`
set 'hlsearch' ('hls' highlight) &  'incsearch' ('is' partial match) option (for searches) (**command mode
**) `:set hls is`
set ignore case option off (**command mode**)  `:set noic`
set 'hlsearch' &  'incsearch' option to off (**command mode**) `:nohlsearch`
set ignore case for just one search command (**command mode**) `/<word>\c`

### Completion

(**command mode**) type a letter and hit `ctrl-d` will bring up a list of commands that begin with that letter and then
type until unique and then hit `<tab>` to complete

## NVChad {collapsible="true" default-state="expanded"}

- change themes: `space t h`
- open tree view: `ctrl + n`
- create a new file: navigate to the directory and press the `a` key, then type in the name of the new file
- open a file: navigate to the file and press `enter` while on the file
- move from one window to another
    - toggle between open windows: `ctrl + w w`
    - move to bottom left, bottom, top, right: `ctrl + w h j k l`
    - move to bottom left, bottom, top, right: `ctrl + w` followed by the left, down, up right arrows
