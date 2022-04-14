# Section 3 - Object-Oriented Java (Classes)

Learn Java by Codecademy

**Reference:** https://www.codecademy.com/courses/learn-java/lessons/java-introduction-to-classes/

# Introduction to Classes

All Java programs require one or more classes that act as a model for the world.

For example, a program to track student test scores might have `Student`, `Course`, and `Grade` classes.

Classes are a blueprint for objects, where blueprints detail the general structure.

In the above example, we represent each student as an *instance*, or *object*, of the `Student` class.

This is called *object-oriented programming* because programs are built around objects and their interactions. An object contains state and behavior.

<br>

# Classes: Syntax

A *class* is the set of instructions that describe how an instance can behave and what information it contains.

**Example** - Declaring a `class` named `Car`:

```java
public class Car {
// scope of Car class starts after curly brace
 
  public static void main(String[] args) {
    // scope of main() starts after curly brace
 
    // program tasks...
 
  }
  // scope of main() ends after curly brace
 
}
// scope of Car class ends after curly brace
```
This class has a `main()` method, which lists the tasks performed by the program. `main()` runs when we execute the compiled Car.class file.

**Note:** `public` is an *access level modifier* that allows **other** classes to interact with this class.

<br>

# Classes: Constructors

In order to create an object (an instance of a class), we need a constructor method. The constructor is defined within the class.

**Example** - Constructor method inside a class:

```java
public class Car {
  // Constructor method
  // The constructor, Car(), shares the same name as the class.
  public Car() {
    // instructions for creating a Car instance
  }  
 
  public static void main(String[] args) {
    // body of main method
  }
}
```

To create an instance, we need to *call* or *invoke* the constructor within main():

```java
public class Car {
 
  public Car() {
    // instructions for creating a Car instance
  }
 
  public static void main(String[] args) {
    // Invoke the constructor
    Car ferrari = new Car(); 
  }
}
```

**Note:** Instead of being declared with a primitive data type like `int` or `boolean`, our variable `ferrari` is declared as a *reference data type*. This means that the value of our variable is a reference to an instance’s memory address. During its declaration, the class name is used as the variable’s type. In this case, the type is `Car`.

The constructor method: `Car()` is invoked using the keyword `new` to indicate that we're creating an instance. **Omitting `new` will cause an error.**

If we were to output the value of `ferrari` we would see a similar memory address:

```
Car@76ed5528
```

The first part, `Car`, refers to the class, and the second part `@76ed5528` refers to the instance’s location in the computer’s memory.

<br>

# Classes: Instance Fields

When an object is created, the constructor sets the initial state of the object. The *state* is made up of associated data that represents the characteristics of an object.

We can add data to an object by introducing *instance variables*, or *instance fields*.

Often times, instance variables are described as a “has-a” relationship with the object. For example, a `Car` “has-a” color. Another way to think of this is that instance variables are the nouns and adjectives associated with an object.

**Example** - Declaring a `String color` instance field:

```java
public class Car {
  // declare fields inside the class
  // by specifying the type and name
  String color;
 
  public Car() {
    // instance fields available in
    // scope of constructor method
  }
 
  public static void main(String[] args) {
    // body of main method
  }
}
```

Fields are a type of state each instance will possess. One instance may have `"red"` as its `color`, another `"blue"`, etc. It’s the job of the constructor to give these instance fields initial value.

<br>

# Classes: Constructor Parameters

In order to assign a value to an instance variable, we need to alter our constructor method to include parameters so that it can access the data we want to assign to an instance.

**Example** - Adding a parameter to the `Car` constructor:

