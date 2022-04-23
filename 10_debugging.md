# Section 10 - Debugging

Learn Java by Codecademy

**Reference:** https://www.codecademy.com/courses/learn-java/lessons/java-debugging/

# Introduction to Bugs

In Java, there are many different ways of classifying errors, but they can be boiled down to three categories:

* **Syntax errors:** Errors found by the compiler.
* **Run-time errors:** Errors that occur when the program is running.
* **Logic errors:** Errors found by the programmer looking for the causes of erroneous results.

<br>

# Syntax Errors

*Syntax errors* represent grammar errors in the use of the programming language. The compiler will tell you where it got into trouble, and its best guess as to what you did wrong.

Some common syntax errors are:

* Misspelled variable and method names.
* Omitting semicolons `;`.
* Omitting closing parenthesis `)`, square bracket `]`, or curly brace `}`.

**Example** - Syntax error message:

```
Debug.java:5: error: ';' expected
  int year = 2019
                  ^
1 error
```

**Note:** Usually the error is on the exact line indicated by the compiler, or the line just before it; however, if the problem is incorrectly nested braces, the actual error may be at the beginning of the nested block.

<br>

# Run-time Errors

*Run-time errors* occur when a program with no compile-time errors asks the computer to do something that the computer is unable to reliably do.

Some common run-time errors:

* Division by zero also known as division error.
* Trying to open a file that doesn’t exist.

**Example** - Run-time error message:

```
Exception in thread "main"
java.lang.ArithmeticException: / by zero
        at Debug.main(Debug.java:8)
```

<br>

# Exceptions

*Exceptions* are the conditions that occur at runtime and may cause the termination of the program.

When this occurs, Java displays a message that includes the name of the exception, the line of the program where the exception occurred, and a stack trace. The stack trace includes:

* The method that was running,
* The method that invoked it,
* The method that invoked that one,
* etc...

Some common exceptions are:

* `ArithmeticException`: Something went wrong during an arithmetic operation; for example, division by zero.
* `NullPointerException`: You tried to access an instance variable or invoke a method on an object that is currently `null`.
* `ArrayIndexOutOfBoundsException`: The index you are using is either negative or greater than the last index of the array (i.e., `array.length - 1`).
* `FileNotFoundException`: Java didn’t find the file it was looking for.

<br>

# Exception Handling

Exception handling is an essential feature of Java programming that allows us to use run-time error exceptions to make our debugging process a little easier.

One way to handle exceptions is using the `try` / `catch`:

* The `try` statement allows you to define a block of code to be tested for errors while it is being executed.
* The `catch` statement allows you to define a block of code to be executed if an error occurs in the try block.

**Example** - `try` & `catch` syntax:

```java
try {

  //  Block of code to try

} catch (NullPointerException e) {
 
  // Print the error message like this:
  System.err.println("NullPointerException: " + e.getMessage());
 
  // Or handle the error another way here

}
```

**Note:** `System.err.println()` will print to the standard error and the text will be in red.

Exceptions can also be chained together:

```java
try {
 
  //  Block of code to try
 
} catch (NullPointerException e) {
 
  //  Code to handle a NullPointerException
 
} catch (ArithmeticException e) {
 
  //  Code to handle an ArithmeticException
 
}
```

You can learn more about exceptions and handling them [here](https://docs.oracle.com/javase/tutorial/essential/exceptions/index.html).

<br>

# Logic Errors

*Logic errors* occur when there is a design flaw in your program that results in the incorrect output.

Some common logic errors:

* Program logic is flawed.
* Some “silly” mistake in an `if` statement or a `for` / `while` loop.
