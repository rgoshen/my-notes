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

## Common Problems (and Their Solutions)

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

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
