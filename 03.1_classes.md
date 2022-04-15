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

In order to create an object (an instance of a class), we **need** a constructor method. The constructor is defined within the class.

**Example** - Constructor method inside a class:

```java
public class Car {
  // Constructor method
  // The constructor, Car(), shares the same name as the class.
  public Car() {
    // instructions for creating a Car instance goes here...
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

The first part, `Car`, refers to the class, and the second part, `@76ed5528`, refers to the instance’s location in the computer’s memory.

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

# Classes: Constructor Parameters & Overloading

## Constructor Parameters

In order to assign a value to an instance variable, we need to alter our constructor method to include parameters so that it can access the data we want to assign to an instance.

**Example** - Adding a parameter to the `Car` constructor:

```java
public class Car {
  String color;
  // constructor method with a parameter
  public Car(String carColor) {
    // parameter value assigned to the field
    color = carColor;
  }
  public static void main(String[] args) {
    // program tasks
  }
}
```

Our method also has a *signature* which defines the name and parameters of the method. In the above example, the signature is `Car(String carColor)`.

## Contructor Overloading

In Java, because of *constructor overloading*, a class can have multiple constructors as long as they have different parameter values. The signature is useful in that it helps the compiler differentiate between the different methods. For example:

```java
public class Car {
  String color;
  int mpg;
  boolean isElectric;
 
  // constructor 1
  public Car(String carColor, int milesPerGallon) {
    color = carColor;
    mpg = milesPerGallon;
  }
  // constructor 2
  public Car(boolean electricCar, int milesPerGallon) {
    isElectric = electricCar;
    mpg = milesPerGallon;
  }
}
```

When we initialize an object, the compiler will know which constructor to use because of the values we pass into it.

For example, `Car myCar = new Car(true, 40)` will be created by 'constructor 2' because the arguments match the type and order of the second constructor’s signature.

If we do not define a constructor, the Java compiler will generate a default constructor that contains no arguments and assigns the object default values. Default values can be created by assigning values to the instance fields during their declaration:

```java
public class Car {
  String color = "red";
  boolean isElectric = false;
  int cupHolders = 4;
 
  public static void main(String[] args) {
    Car myCar = new Car();
    System.out.println(myCar.color); // Prints: red
  }
}
```

<br>

# Classes: Assigning Values to Instance Fields

Now that our constructor has a parameter, we must pass values into the method call. These values are referred to as *arguments*; once they are passed in, they will be used to give the instance fields initial value.

**Example** - Passing the String value `"red"` to our constructor method call `new Car("red");`:

```java
public class Car {
  String color;
 
  public Car(String carColor) {
    // assign parameter value to instance field
    color = carColor;
  }
 
  public static void main(String[] args) {
    // parameter value supplied when calling constructor
    Car ferrari = new Car("red");
  }
}
```

**Note:** The type of the value given to the invocation **must** match the type declared by the parameter.

We can access the value of the `color` field with the dot operator ( `.` ):

```java
ferrari.color;
// "red"
```

<br>

# Classes: Multiple Fields

Objects are not limited to a single instance field. We can declare as many fields as are necessary for the requirements of our program.

**Example** - Multiple instance fields & constructor method parameters:

```java
public class Car {
  String color;
  // additional fields
  boolean isRunning;
  int velocity;
 
  // additional parameters that correspond to the new fields
  public Car(String carColor, boolean carRunning, int milesPerHour) {
    color = carColor;
    // assign new parameters to the new fields
    isRunning = carRunning;
    velocity = milesPerHour;
  }
 
  public static void main(String[] args) {
    // additional values passed into the method call
    Car ferrari = new Car("red", true, 27);
    Car renault = new Car("blue", false, 70);
 
    System.out.println(renault.isRunning);
    // false
    System.out.println(ferrari.velocity);
    // 27
  }
}
```

**Note:** Ordering matters! We **must** pass values into the constructor invocation in the same order that they’re listed in the parameters.
