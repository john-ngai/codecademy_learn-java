# Section 2 - Variables

Learn Java by Codecademy

**Reference:** https://www.codecademy.com/courses/learn-java/lessons/learn-java-variables/

# Introduction to Variables

In Java, we specify the type of information we’re storing.

*Primitive datatypes* are types of data built-in to the Java system. The three main primitive types we’ll cover are `int`, `double`, and `boolean`.

Declaring a variable requires that we specify the **type** and **name**:

```java
// Syntax: datatype variableName

int age;
double salaryRequirement;
boolean isEmployed;
```

To assign a value to a variable, we use the assignment operator ( `=` ):

```java
age = 85;
```

**Note:** When code is used to represent a fixed value, like 85, it is referred to as a *literal*.

It’s also common to declare a variable and assign it a value within a single line of code:

```java
int yearCodecademyWasFounded = 2011;
```

<br>

# int

Whole numbers are stored in the `int` primitive data type.

An `int` can hold positive numbers, negative numbers, and zero. They **do not** store fractions or numbers with decimals in them.

The `int` data type allows values between -2,147,483,648 and 2,147,483,647, inclusive.

**Examples**

```java
// int variable declaration
int yearJavaWasCreated;

// assignment
yearJavaWasCreated = 1996;

// declaration and assignment
int numberOfPrimitiveTypes = 8;
```

<br>

# doubles

A `double` can hold decimals as well as very large and very small numbers.

The maximum value is 1.797,693,134,862,315,7 E+308, and the minimum value is 4.9 E-324!

**Examples**

```java
// doubles can have decimal places:
double price = 8.99;

// doubles can have values bigger than what an int could hold:
double gdp = 12237700000;
```

<br>

# booleans

The `boolean` data type references one of two values: `true` or `false`.

**Examples**

```java
boolean javaIsACompiledLanguage = true;
boolean javaIsACupOfCoffee = false;
```

<br>

# char

The `char` data type can hold any character, like a letter, space, or punctuation mark.

It **must** be surrounded by single quotes, `'`.

**Examples**

```java
char grade = 'A';
char firstLetter = 'p';
char punctuation = '!';
```

<br>

# String

## String Declarations

The `String` object holds a sequence of characters.

Unlike the primitive data types mentioned above, the `String` is an object, where objects have built-in behavior.

There are two ways to create a `String` object: 1) using a `String` literal or 2) calling the `String` class to create a new `String` object.

**Example 1** - String declaration using a String literal:

A *String literal* is any sequence of characters enclosed in double-quotes (`""`).

```java
String greeting = "Hello World";
```

**Example 2** - String declaration by calling the `String` class:

```java
String salutations = new String("Hello World");
```

**Note:** There are subtle differences in behavior depending on whether you create a `String` using a `String` literal or a new `String` object. We’ll dive into those later, but for now, we’ll almost always be using `String` literals.

## Escape Sequences

Certain symbols, known as escape sequences, have an alternative use in Java print statements. Escape characters begin with the character `\`.

There are three common escape sequences that you should be aware of:

1. The `\"` escape sequence allows us to add quotation marks ( `"` ) to a `String` value. :

```java
System.out.println("\"Hello World\"");
// Prints: "Hello World"
```

2. Using the `\\` escape sequence allows us to place backslashes in our `String` text:

```java
System.out.println("This is the backslash symbol: \\");
// Prints: This is the backslash symbol: \
```

3. Finally, if we place a `\n` escape sequence in a `String`, the compiler will output a new line of text:

```java
System.out.println("Hello\nGoodbye");
/*
Prints:
  Hello
  Goodbye
*/
```

<br>

# Static Checking

The Java programming language has *static typing*. Java programs will not compile if a variable is assigned a value of an incorrect type. This is a *bug*, specifically a *type declaration* bug.

**Example** - The program will not compile if the declared type of the variable does not match the type of the assigned value:

```java
int greeting = "Hello World";
```

Instead, we see the following error in the console at compilation:

```
error: incompatible types: String cannot be converted to int
  int greeting = "Hello World";
```

When bugs are not caught at compilation, they interrupt execution of the code by causing `runtime errors`. The program will crash.

Java’s static typing helps programmers avoid runtime errors, and thus have much safer code that is free from bugs.

<br>

# Naming

In Java, variable names are case-sensitive. For example, `myHeight` is a different variable from `myheight`.

A variable can start with a valid letter, dollar sign ( `$` ), or underscore ( `_` ). No other symbols or numbers can begin a variable name! For example `1stPlace` and `*Gazer` are not valid variable names.

Java variables use the *camelCase* style of capitalization.

**Examples**

```java
// good style
boolean isHuman;
 
// bad styles
// no capitalization for new word
boolean ishuman;
// first word should be lowercase
boolean IsHuman;
// underscores don't separate words
boolean is_human;
```
