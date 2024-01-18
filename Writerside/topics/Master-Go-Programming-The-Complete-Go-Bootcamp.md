# Master Go Programming: The Complete Go Bootcamp

**incomplete**

## Getting Started

### GOPATH and Code Organization

- Go requires you to organize your code in a specific way
- Go programmers typically keep all their code in a single workspace
- A workspace is nothing more than a directory in your file system whose path is stored in an environment variable
  called `GOPATH`
- On windows, it's in `%USERPROFILE%\go`
- On Macs & Linux, it's in `~go`
- You can print out the values of the environment variables by running the `go env` command

### Go Workspace (`GOPATH`)

The work directory (`GOTPATH`) contains the following 3 subdirectories at its root:

1. `src`: contains the source files for your own or other downloaded packages
2. `pkg`: contains go package objects (aka package archives)
    - these are non-executable files or shared libraries ending in `.a`
3. `bin`: contains compiled & executable Go programs
    - when you run `go install` on a program directory, Go will put the executable file under this file

- To run/compile programs (CLI): `go run <filename.go>`

### Compiling (`go build`) & Running Go Applications (`go run`)

**go** is a tool for managing Go source code

1. `go run`: compiles & runs the application
    - it doesn't produce an executable
    - `go run <filename.go>` compiles & immediately runs the Go program
    - `go run -x <filename.go>` gives details about the compilation process
2. `go build`: it just compiles the application
    - produces an executable
    - `go build <filename.go>` compiles a bunch of Go source files
    - compiles packages and dependencies
    - `go build` will compile the files in the current directory and will produce an executable file with
      the name of the current working directory
    - `go build -o app` produces an executable file called _app_

> before running `go build` for the first time run `go mod init` to enable dependency tracking for your code

- compiling for windows: `GOOS=windows GOARCH=amd64 go build -o winapp.exe`
- compiling for linux: `GOOS=linux GOARC=amd64 go build -o linuxapp`
- compiling for mac:  `GOOS=darwin GOARCH=amd64 go build -o macapp`

3. `go install`

- both `go install` & `go build` will compile the package in the current directory
- if the package is main, `go build` will place the resulting executable in the current directory and `go install` will
  move the executable to **`GOPATH/src`**

> when running `go install` you use the paths relative to **`GOPATH/src`**

{style="note"}

### Formatting Go Source Code (`gofmt`)

- Go strongly suggests certain styles
- `gofmt` which comes from **golang formatter** will format a program's source code in an idiomatic way that is easy to
  read and understand
- `gofmt` is built into the language runtime and it formats Go code according to a set of stable, well-understood
  language rules
- can be run manually at the command line or can configure our IDE to rub `gofmt` each time a file is saved

_Example:_
`gofmt -l -w main.go`

- `-l`: tells you which file was modified
- `-w`: if not formatted correctly, will overwrite file

- if you run `gofmt` in the directory, all source files will be formatted correctly

## Go Basics

### Variables in Go

- a variable is a name for a memory location where a value of a specific type is stored
- a variable belongs and it's created **at runtime**
- a declared variable **MUST** be used or get an error!
- `_` is the **blank identifier** and mutes the compile time error returned by unusual variables

**Declaring variables:**

1. using the `var` keyword

```Go
var x int = 7

var sl string
sl = "Learning Go!"
```

2. using the Short Declaration Operator (`:=`)

```Go
age := 30
```

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
