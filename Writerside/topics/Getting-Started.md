# Getting Started

This trail provides everything you'll need to know about getting started with the Java programming language.

## The Java Technology Phenomenon

### About the Java Technology

- both a programming language and a platform

#### The Programming Language

- all source files written in plain text files ending in `.java` extension
- these source files are then compiled by the javac compiler into files containing bytecode and ending in `.class`
  extension
    - this bytecode is not native to any particular processor
    - only native to the machine language of Java Virtual Machine (JVM)
- Java launcher tool then runs the application inside an instance of the JVM

![overview of the java software development process](java-software-development-process.jpg)

- JVM will be available on any operating system, same `.class` file is capable of being used
- some JVMs, such
  as [Java SE HotSpot at a Glance](https://www.oracle.com/java/technologies/javase/javase-core-technologies-apis.html),
  performs additional steps at runtime will give the application a performance boost
    - includes various tasks such as finding performance bottlenecks and recompiling (to native code) frequently used
      sections of code

![JVM architecture neutral](JVM-architecture-neutral.jpg)

#### The Java Platform

The Java <tooltip term="platform">platform</tooltip> has two components:

- the _Java Virtual Machine_ (JVM)
- the _Java Application Programming Interface_ (<tooltip term="api">API</tooltip>)
    - grouped into libraries of related classes and interfaces
    - libraries are known as packages

![java platform](java_platform.jpg)

### What Can the Java Technology Do?

The general-purpose, high-level Java programming language is a powerful software platform. Every full implementation of
the Java platform gives you the following features:

- **Development Tools**: The development tools provide everything you'll need for compiling, running, monitoring,
  debugging, and documenting your applications. As a new developer, the main tools you'll be using are the javac
  compiler, the java launcher, and the javadoc documentation tool.
- **Application Programming Interface (API)**: The API provides the core functionality of the Java programming language.
  It offers a wide array of useful classes ready for use in your own applications. It spans everything from basic
  objects, to networking and security, to XML generation and database access, and more. The core API is very large; to
  get an overview of what it contains, consult the Java Platform Standard Edition 8 Documentation.
- **Deployment Technologies**: The JDK software provides standard mechanisms such as the Java Web Start software and
  Java Plug-In software for deploying your applications to end users.
- **User Interface Toolkits**: The JavaFX, Swing, and Java 2D toolkits make it possible to create sophisticated
  Graphical User Interfaces (GUIs).
- **Integration Libraries**: Integration libraries such as the Java IDL API, JDBC API, Java Naming and Directory
  Interface (JNDI) API, Java RMI, and Java Remote Method Invocation over Internet Inter-ORB Protocol Technology (Java
  RMI-IIOP Technology) enable database access and manipulation of remote objects.

### How will the Java Technology Change My Life?

Java will likely to make your programs better and requires less effort than other languages by helping to do the
following:

- **Get started quickly**: Although the Java programming language is a powerful object-oriented language, it's easy to
  learn, especially for programmers already familiar with C or C++.
- **Write less code**: Comparisons of program metrics (class counts, method counts, and so on) suggest that a program
  written in the Java programming language can be four times smaller than the same program written in C++.
- **Write better code**: The Java programming language encourages good coding practices, and automatic garbage
  collection helps you avoid memory leaks. Its object orientation, its JavaBeans™ component architecture, and its
  wide-ranging, easily extendible API let you reuse existing, tested code and introduce fewer bugs.
- **Develop programs more quickly**: The Java programming language is simpler than C++, and as such, your development
  time could be up to twice as fast when writing in it. Your programs will also require fewer lines of code.
- **Avoid platform dependencies**: You can keep your program portable by avoiding the use of libraries written in other
  languages.
- **Write once, run anywhere**: Because applications written in the Java programming language are compiled into
  machine-independent bytecodes, they run consistently on any Java platform.
- **Distribute software more easily**: With Java Web Start software, users will be able to launch your applications with
  a single click of the mouse. An automatic version check at startup ensures that users are always up to date with the
  latest version of your software. If an update is available, the Java Web Start software will automatically update
  their installation.

## The "Hello World!" Application

1. In your favorite editor/IDE create a file called `HelloWorldApp.java` and write the following code inside that file:

```Java
```

{src="HelloWorldApp.java"}

2. Compile the above file into a `.class` file

```Bash
javac HelloWorldApp.java
```

3. Run the "HelloWord" app

<compare first-title="Windows" second-title="Unix based">
<code-block lang="bash">
java -cp HelloWorldApp
</code-block>
<code-block lang="bash">
java HelloWorldApp
</code-block>
</compare>

4. You should see the following output:

```Bash
Hello World!
```

## A Closer Look at the "Hello World!" Application

The "Hello World" app consists of three main components:

1. Source code comments
2. HelloWorldApp class definition
3. main method

### Source code comments

```java
/**
 * The HelloWorldApp class implements an application that
 * simply prints "Hello World!" to standard output.
 */
```

- comments are ignored by the compiler
- there are three different kinds of comments in Java
    1. multi-line: `/* text */` - java compiler ignores everything between `/* */`
    2. documentation: `/** documentation */` - indicates a documentation comment
        - [javadoc tool](https://docs.oracle.com/javase/8/docs/technotes/guides/javadoc/index.html) uses doc comments
          when preparing automatically generated documentation
    3. single line: `// text` - compiler ignores everything from // to the end of the line

### Class Definition

```java
class HelloWorldApp {
    
}
```

- keyword `class` begins the class definition for a class named `HelloWorldApp`
- code for each class appears between the opening and closing curly braces (`{}`)

### The main method

```java
    public static void main(String[] args) {
        System.out.println("Hello World!"); // Display the string.
    }
```

- every application must contain a `main` method whose signature is: `public static void main(String[] args)`
- modifiers `public` and `static` can be written in either order (`public static` or `static public`), but the
  convention is to use `public static` as shown above
- you can name the argument anything you want, but most programmers choose "args" or "argv"
- `main` method is the entry point for your application and will subsequently invoke all the other methods required by
  your program
- it accepts a single argument: an array of elements of type `String`
- this array is the mechanism through which the runtime system passes information to your application
- for example: `java MyApp arg1 arg2`
- each string in the array is called a _command-line argument_
- _command-line arguments_ let users affect the operation of the application without recompiling it
- the "Hello World!" application ignores its command-line arguments, but you should be aware of the fact that such
  arguments do exist

Finally the line: `System.out.println("Hello World!");`

- ses the `System` class from the core library to print the "Hello World!" message to standard output

## Common Problems (and Their Solutions)

### Compiler Problems

#### Common Error Messages on Microsoft Windows Systems

- `javac` is not recognized as an internal or external command, operable program or batch file

If you receive this error, Windows cannot find the compiler (javac).

Here's one way to tell Windows where to find javac.
Suppose you installed the JDK in `C:\jdk1.8.0`.
At the prompt you would type the following command and press Enter:

`C:\jdk1.8.0\bin\javac HelloWorldApp.java`

If you choose this option, you'll have to precede your javac and java commands with `C:\jdk1.8.0\bin\` each time you
compile or run a program. To avoid this extra typing, consult the
section [Updating the PATH variable](https://docs.oracle.com/javase/8/docs/technotes/guides/install/windows_jdk_install.html#BABGDJFH)
in the JDK 8 installation instructions.

- Class names, `HelloWorldApp`, are only accepted if annotation processing is explicitly requested

If you receive this error, you forgot to include the `.java` suffix when compiling the program. Remember, the command is
`javac HelloWorldApp.java` not `javac HelloWorldApp`.

#### Common Error Messages on UNIX Systems

- `javac: Command not found`

If you receive this error, UNIX cannot find the compiler, `javac`.

Here's one way to tell UNIX where to find javac.
Suppose you installed the JDK in `/usr/local/jdk1.8.0`.
At the prompt you would type the following command and press Return:

`/usr/local/jdk1.8.0/javac HelloWorldApp.java`

> **Note**: If you choose this option, each time you compile or run a program, you'll have to precede your javac and
> java commands with /usr/local/jdk1.8.0/. To avoid this extra typing, you could add this information to your PATH
> variable. The steps for doing so will vary depending on which shell you are currently running.

{style="note"}

- Class names, `HelloWorldApp`, are only accepted if annotation processing is explicitly requested

If you receive this error, you forgot to include the `.java` suffix when compiling the program. Remember, the command is
`javac HelloWorldApp.java` not `javac HelloWorldApp`.

#### Syntax Errors (All Platforms)

If you mistype part of a program, the compiler may issue a syntax error. The message usually displays the type of the
error, the line number where the error was detected, the code on that line, and the position of the error within the
code. Here's an error caused by omitting a semicolon (;) at the end of a statement:

```Bash
Testing.java:8: error: ';' expected
            count++
                   ^
1 error
```

If you see any compiler errors, then your program did not successfully compile, and the compiler did not create
a `.class` file. Carefully verify the program, fix any errors that you detect, and try again.

#### Semantic Errors

In addition to verifying that your program is syntactically correct, the compiler checks for other basic correctness.
For example, the compiler warns you each time you use a variable that has not been initialized:

```Bash
Testing.java:8: error: variable count might not have been initialized
            count++;
            ^
Testing.java:9: error: variable count might not have been initialized
        System.out.println("Input has " + count + " chars.");
                                          ^
2 errors
```

Again, your program did not successfully compile, and the compiler did not create a `.class` file. Fix the error and try
again.

### Runtime Problems

#### Error Messages on Microsoft Windows Systems

- Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorldApp

If you receive this error, java cannot find your bytecode file, `HelloWorldApp.class`.

One of the places java tries to find your bytecode file is your current directory. So, for example, if your bytecode
file is in /home/jdoe/java, you should change your current directory to that. To change your directory, type the
following command at the prompt and press Return:

`cd /home/jdoe/java`

If you enter `pwd` at the prompt, you should see `/home/jdoe/java`. If you enter `ls` at the prompt, you should see
your `.java` and `.class` files. Now enter `java HelloWorldApp` again.

If you still have problems, you might have to change your `CLASSPATH` environment variable.
To see if this is necessary, try clobbering the classpath with the following command.

`unset CLASSPATH`

Now enter `java HelloWorldApp` again.
If the program works now, you'll have to change your `CLASSPATH` variable in the same
manner as the `PATH` variable above.

#### Error Messages on UNIX Systems

- Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorldApp/class

A common mistake made by beginner programmers is to try and run the java launcher on the `.class` file that was created
by the compiler. For example, you'll get this error if you try to run your program with `java HelloWorldApp.class`
instead of `java HelloWorldApp`. Remember, the argument is the name of the class that you want to use, not the filename.

- Exception in thread "main" java.lang.NoSuchMethodError: main

The Java VM requires that the class you execute with it have a `main` method at which to begin execution of your
application. [A Closer Look at the "Hello World!" Application](#a-closer-look-at-the-hello-world-application) discusses
the main method in detail.

#### Applet or Java Web Start Application Is Blocked

If you are running an application through a browser and get security warnings that say the application is blocked, check
the following items:

- Verify that the attributes in the JAR file manifest are set correctly for the environment in which the application is
  running. The Permissions attribute is required. In a NetBeans project, you can open the manifest file from the Files
  tab of the NetBeans IDE by expanding the project folder and double-clicking `manifest.mf`.
- Verify that the application is signed by a valid certificate and that the certificate is located in the Signer CA
  keystore.
- If you are running a local applet, set up a web server to use for testing. You can also add your application to the
  exception site list, which is managed in the Security tab of the Java Control Panel.

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
