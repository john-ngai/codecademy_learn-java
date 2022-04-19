# Section 7 - String Methods

Learn Java by Codecademy

**Reference:** https://www.codecademy.com/courses/learn-java/lessons/java-string-methods/

# Introduction to String Methods

As you may recall, a `String`, which is widely used in Java, is an object that represents a sequence of characters Since character strings are so vital to programming, Java dedicated an entire class to them.

In this lesson, we will go over several `String` methods:

* length()
* concat()
* equals()
* indexOf()
* charAt()
* substring()
* toUpperCase() / toLowerCase()

<br>

# length()

The `length()` string method returns the total number of characters of a `String`:

```java
String str = "Hello World!";  
 
System.out.println(str.length());
// Output: 12
```

**Note:** In theory, the length of a `String` is the same as the [Unicode](https://en.wikipedia.org/wiki/Unicode) units of the `String`. For example, escape sequences such as `\n` count as only one character.

<br>

# concat()

## Syntax

The `concat()` method concatenates one string to the end of another string (i.e, joins two strings together):

```java
String name = new String("Code");

name = name.concat("cademy");
 
System.out.println(name);
// Output: Codecademy
```

## Immutable Objects

In Java, a `String` is an *immutable object*, meaning that `String` methods, like `concat()` do not actually change a String object.

In the previous example, the `name` variable holds a **reference** to the `String` object, `"Code"`. When we use `concat()` on `name`, we changed it's value so that it **references** a new object — `"Code"`, combined with the String literal, `"cademy"`.

Suppose we do something slightly different. We’ll use `concat()` on `name` without reassigning its value:

```java
String name = "Code";
 
name.concat("cademy");
 
System.out.println(name);
// Output: Code
```

`Code` would be printed instead. Therefore, the value of the `String` can’t change! Instead, we need to create a new object and assign that new object to some variable.

<br>

# equals()

With objects, such as `Strings`, we can’t use the primitive equality operator `==` to check for equality between two strings. To test equality with strings, we use a built-in method called `equals()`:

```java
String flavor1 = "Mango";
String flavor2 = "Peach";
 
System.out.println(flavor1.equals("Mango"));
// prints true
 
System.out.println(flavor2.equals("Mango"));
// prints false
```

**Note:** There’s also an `equalsIgnoreCase()` method that compares two strings without considering upper/lower cases.

<br>

# indexOf()

If we want to know the index of the **first occurence** of a character in a string, we can use the `indexOf()` method on a string:

```java
String letters = "ABCDEFGHIJKLMN";
 
System.out.println(letters.indexOf("C"));
// Output: 2
```

We can also use `indexOf()` to find the **first occurence** of an entire substring:

```java
String letters = "ABCDEFGHIJKLMN";
 
System.out.println(letters.indexOf("EFG"));
// Output: 4
```

**Note:** If the `indexOf()` doesn’t find what it’s looking for, it’ll return a `-1`.

<br>

# charAt()

The `charAt()` method returns the character located at the specified index:

```java
String str = "qwer";
 
System.out.println(str.charAt(2));
// Output: e
```

**Note:** In the above example, if we try to return the character located at index 4, it would produce an `IndexOutOfBoundsException` error, because index 4 is out of range.

<br>

# substring()

As it's name suggests, the `substring()` method extracts a *substring* from a string:

```java
String line = "The Heav'ns and all the Constellations rung";
 
System.out.println(line.substring(24));
// Output: Constellations rung
```

If we want a substring from the middle of the string, we can call `substring()` with two arguments instead. The first argument is *inclusive* and the second is *exclusive*.

```java
String line = "The Heav'ns and all the Constellations rung";
 
System.out.println(line.substring(27, 33));
// Output: stella
```

Lastly, we can also use the `substring()` method to return a single-element substring at a specific index:

```java
String line = "The Heav'ns and all the Constellations rung";
 
System.out.println(line.substring(24, 25));
// Output: C
```

<br>

# toUpperCase() / toLowerCase()

`toUpperCase()` returns the string value converted to uppercase, and `toLowerCase()` returns the string value converted to lowercase:

```java
String input = "Cricket!";
 
String upper = input.toUpperCase();
// stores "CRICKET!"
 
String lower = input.toLowerCase();
// stores "cricket!"
```

**Tip:** A good use of this functionality is to ensure consistency of the data you store in a database. Making sure all of the data you get from a user is lowercase before you store it in your database will make your database easier to search through later.
