# C Programming: A Modern Approach

**incomplete**

## C Fundamentals {collapsible="true" default-state="expanded"}

### Writing a Simple Program

```cs
// pun.c

#include<stdio.h>

int main(void)
{
    printf("To C, or not to C: that is the question.\n");
    return 0;
}
```

- `#include<stdio>` necessary to "include" information about C's standard I/O (input/output) library
- program's executable code goes inside `main`, which represents the "main" program
- `printf` is a function from the standard I/O library that produces a nicely formatted output
- `\n` tells `printf` to advance to the next line after printing the message
- `return 0;` indicates the program "returns" the value 0 to the operating system when it terminates

### Compiling and Linking

1. create a file name pun.c containing the program
2. convert the program to a form that the machine can executable
    1. **Preprocessing.** the program is given to a preprocessor which obeys commands that begin with # (known as *
       *directives**)
    2. **Compiling.** modified program now goes to a **compiler**, which translates it into machine instructions (*
       *object code**)
    3. **Linking.** a **linker** combines the object code produced by the compiler with any additional code needed to
       yield a complete executable program. This additional code includes library functions (like printf) that are used
       in the program

All this is usually automated. In fact, the preprocessor is usually integrated with the compiler.

The commands necessary to compile and link are:

```bash
gcc -o pun pun.
```

<seealso>
    C Programming: A Modern Approach by K. N. King
</seealso>