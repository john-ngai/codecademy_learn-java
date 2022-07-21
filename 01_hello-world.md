# Section 1 - Hello World

Learn Java by Codecademy

**Reference:** https://www.codecademy.com/courses/learn-java/lessons/hello-world-java/

# Introduction to Java

Sun Microsystems released the Java programming language in 1995.

One reason people love Java is because of the *Java Virtual Machine*, which ensures the same Java code can be run on different operating systems and platforms.

**Example** - A simple program written in Java:

```java
// HelloWorld.java

public class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```
<br>

# Hello Java File!

## Classes

Inside the previous `HelloWorld.java` example, we had a class:

```java
public class HelloWorld {

}
```

For now, think of classes as a **single** concepts.
We marked the domain of a class (concept) using curly braces: `{}`.

**Important:** Each file has *one* primary class named after the file. In the above example, the primary class is `HelloWorld`, so the file name should be `HelloWorld.java`. Every word is capitalized.

## main() Method

Inside the class we had a `main()` method which lists our program tasks:

```java
public static void main(String[] args) {

}
```

Like classes, we used curly braces to mark the beginning and end of a method.

`public`, `static`, and `void` are syntax we’ll learn about in future lessons.

`String[] args` is a placeholder for information we want to pass into our program. This syntax is necessary for the program to run, but more advanced than we need to explore at the moment.

<br>

# Print Statements

Let’s take a closer look at this instruction from our previous program:

```java
System.out.println("Hello World");
```

Print statements output information onto the screen (also referred to as the output terminal).

Broken down:

* `System` is a built-in Java class that contains useful tools for our programs.
* `out` is short for "output".
* `println` is short for "print line".

We can use `System.out.println()` whenever we want the program to create a *new line* on the screen after outputting a value:

```java
System.out.println("Hello World");
System.out.println("Today is a great day to code!");

/*
Output:
  Hello World
  Today is a great day to code!
/*
```

We also can output information using `System.out.print()`. Unlike `System.out.println()`, this type of print statement outputs everything onto the same line.

```java
System.out.print("Hello ");
System.out.print("World");

/*
Output:
  Hello World
/*
```

**Note:** if you were to use `print()` or `println()` again, the new text will print immediately after `World` on the **same** line.

<br>

# Commenting Code

When comments are short we use the single-line syntax: `//`.

```java
// calculate customer satisfaction rating
```

When comments are long we use the multi-line syntax: `/*` and `*/`.

```java
/*
We chose to store information across multiple databases to
minimize the possibility of data loss. We'll need to be careful
to make sure it does not go out of sync!
*/
```

Another type of commenting option is the *Javadoc* comment which is represented by `/**` and `*/`. Javadoc comments are used to create documentation for APIs (Application Programming Interfaces).

Javadoc comments are typically written before the declaration of fields, methods, and classes:

```java
/**
* The following class accomplishes the following task...
*/
```

**Example** - How a comment would look in a complete program:

```java
/**
* The following class shows what a comment would look like in a program.
*/
public class CommentExample {
  // I'm a comment inside the class
  public static void main(String[] args) {
    // I'm a comment inside a method
    System.out.println("This program has comments!");
  }
}
```

<br>

# Whitespace & Semicolons

## Whitespace

Java **does not** interpret whitespace (the areas of the code without syntax), but humans use whitespace to make code more readable.

Functionally, these two code samples are identical:

```java
// Sample #1
System.out.println("Java");System.out.println("Lava");System.out.println("Guava");

// Sample #2
System.out.println("Java");
 
System.out.println("Lava");
 
System.out.println("Guava");
```

## Semicolons

Unlike whitespace, Java **does** interpret semicolons. Semicolons are used to mark the end of a *statement*, one line of code that performs a single task.

Let’s contrast statements with the curly brace, `{}`. Curly braces mark the **scope** of our classes and methods. There are **no** semicolons at the end of a curly brace.

<br>

# Compilation: Catching Errors & Creating Executables

## Catching Errors

Java is a *compiled* programming language, meaning the code we write in a `.java` file is transformed into *byte* code by a compiler before it is executed by the Java Virtual Machine on your computer.

A compiler is a program that translates human-friendly programming languages into other programming languages that computers can execute.

The compiling process catches mistakes **before** the computer runs our code.

**Note:** The following examples references the command line. Codecademy has a [lesson on the command line](https://www.codecademy.com/learn/learn-the-command-line) if you’d like to learn more.

**Example** - Compile a Java file, `Plankton.java`, using the terminal command:

```
javac Plankton.java
```

A successful compilation produces a `.class` file: `Plankton.class`, that we execute with the terminal command:

```
java Plankton
```

An unsuccessful compilation produces a list of errors. No `.class` file is made until the errors are corrected and the compile command is run again.

## Creating Executables

If the file compiles successfully, this command produces an executable class: `FileName.class`. Executable means we can run this program from the terminal.

**Example 1** - We can run the executable on a file named `Whales.class` with the command:

```
java Whales
```

Notice that we leave off the `.class` part of the filename.

**Example 2** - Full compilation cycle:

```java
// Welcome.java

public class Welcome {
  public static void main(String[] args) {
    System.out.println("Welcome to Codecademy's Java course!");
  }
}
```

We can compile the `Welcome.java` file with the command:

```
javac Welcome.java
```

The terminal shows no errors, which indicates a successful compilation.

We now have two files:

1. `Welcome.java`, our original file with Java syntax.
2. `Welcome.class`, our compiled file with Java bytecode, ready to be executed by the Java Virtual Machine.

We can execute the compiled class with the command:

```
java Welcome
```

The following is printed to the screen:

```
Welcome to Codecademy's Java course!
```
