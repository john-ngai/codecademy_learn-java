# Section 9 - Inheritance & Polymorphism

Learn Java by Codecademy

**Reference:** https://www.codecademy.com/courses/learn-java/lessons/java-inheritance-and-polymorphism/

# Introduction to Inheritance

A Java class can also *inherit* traits from another class.

For example, suppose we build a `Shape` class with a number of fields and methods. Afterwards, if we build a `Triangle` class that shares the same fields and methods as the shape class, in addition to it's own triangle-specific properties, we can define the `Triangle` as also being a `Shape`.

Therefore, the `Triangle` class will *inherit* all the traits of `Shape`, but the `Triangle` can also contain its own unique methods and variables.

There are several terms you’ll encounter frequently in inheritance:

* *Parent class, superclass, and base class* refer to the class that another class inherits from (like `Shape`).
* *Child class, subclass, and derived* class refer to a class that inherits from another class (like `Triangle`).

<br>

# Inheritance in Practice

We can define a child class that inherits from a parent class using `extends` keyword:

```java
class Shape {
  // Shape class members
}
 
class Triangle extends Shape {
  // additional Triangle class members
}
```

When we use inheritance to extend a subclass from a superclass, we create an “is-a” relationship from the subclass to the superclass. For example, an object of `Triangle` *is a* member of the `Shape` class; however, an object of `Shape` is not necessarily an object of `Triangle`.

**Note:** Most Java programs utilize multiple classes, each of which requires its own file. However, only one file needs a `main()` method — this is the file we will run.

<br>

# Inheriting the Constructor

The `super()` method can be used to act like the parent constructor inside the child constructor.

For example, let’s say `Shape` has a `numSides` field that is set by passing an `int` into the constructor. By using the `super()` method, and passing `3` as it's argument, we are making it possible to instantiate a `Triangle` without passing in a value for `numSides`:

```java
class Triangle extends Shape {
  public Triangle() {
    super(3);
  }
}
```

However, it's also possible to write a constructor without making a call to any `super()` constructor:

```java
class Triangle extends Shape {
  public Triangle() {
    this.numSides = 3;
  }
}
```

**Note:** In the above scenario, Java will still secretly call the parent class constructor, `super()`, without any arguements. The `Triangle()` constructor first calls the `Shape()` constructor. That `Shape()` takes care of whatever business it needs to take care of. Then after that is complete, only then is `this.numSides` to set to `3`.

<br>

# Parent Class Access Modifiers

## protected

In addition to the `public` and `private` access modifiers, the `protected` access modifier allows child classes to access otherwise `private` variables and methods within the parent class.

**Example** - A `protected` variable:

```java
class Shape {
  // any child class of Shape can access perimeter
  protected double perimeter;
}
```

## final

If we add `final` before a parent class method’s access modifier, we disable any child classes from changing that method. This can be helpful in limiting bugs that might occur from modifying a particular method.

**Example** - A method prepended with a `final` keyword:

```java
final public boolean isTasty() {
  return true;
}
```

<br>

# Introduction to Polymorphism

In Java, if `Orange` is a `Fruit` through inheritance, you can then use `Orange` in the same contexts as `Fruit` like this:

```java
public String makeJuice(Fruit fruit) {
  return "Apple juice and " + fruit.squeeze();
}
 
// inside main()
Orange orange = new Orange();
System.out.println(juicer.makeJuice(orange));
```

Java incorporates the object-oriented programming principle of *polymorphism*, meaning "many forms". This allows a child class to share the information and behavior of its parent class while also incorporating its own functionality.

The main advantages of polymorphic programming are:

* Simplifying syntax.
* Reducing cognitive overload for developers.

**Note:** The reverse situation is not true; you cannot use a generic parent class instance where a child class instance is required. So an `Orange` can be used as a `Fruit`, but a `Fruit` cannot be used as an `Orange`.

<br>

# Method Overriding

One common use of polymorphism with Java classes is overriding parent class methods in a child class.

For example, let’s say we have a `BankAccount` class that allows us to print the current balance. We want to build a `CheckingAccount` class that inherits the functionality of a `BankAccount` but with a modified `printBalance()` method. As such, we can do the following:

```java
class BankAccount {
  protected double balance;
 
  public BankAccount(double balanceIn){
    balance = balanceIn;
  }
 
  public void printBalance() {
    System.out.println("Your account balance is $" + balance);
  }
}
 
class CheckingAccount extends BankAccount {
 
  public CheckingAccount(double balance) {
    super(balance);
  }
 
  @Override // This keyword informs the compiler that we want to override a method in the parent class.
  public void printBalance() {
    System.out.println("Your checking account balance is $" + balance);
  }
}
```

Notice that in order to properly override `printBalance()`, in `CheckingAccount` the method has the following in common with the corresponding method in `BankAccount`:

* Method name
* Return type
* Number and type of parameters

## Using super to Call the Methods of a Parent Class

 While we now have the ability to override methods from a superclass, we may find ourselves in a unique situation where we want to use the superclass method instead of the subclass’ overridden method.

 If that’s the case, we can call the parent class method by prepending `super` followed by the dot operator ( `.` ) to the method call. Note that this only works if we pass in the proper method parameters.

 **Example** - Calling two versions of `printBalance()`:

 ```java
class CheckingAccount extends BankAccount {
  public CheckingAccount(double balance) {
    super(balance);
  }
 
  @Override
  public void printBalance() {
    System.out.println("Your checking account balance is $" + balance);
  }
 
  public void checkBalances() {
    // calls method from CheckingAccount
    printBalance();

    // calls method from BankAccount
    super.printBalance();
  }
 
  public static void main(String[] args) {
    CheckingAccount myCheckings = new CheckingAccount(5000);
    
    myCheckings.checkBalances();
    /*
    Output:
      Your checking account balance is $5000
      Your account balance is $5000
    */
  }
}
 ```

 <br>

 # Using a Child Class as it's Parent Class

 An important facet of polymorphism is the ability to use a child class object where an object of its parent class is expected.

 One way to do this explicitly is to instantiate a child class object as a member of the parent class:

 ```java
BankAccount kaylasAccount = new CheckingAccount(600.00);
 ```

 In the above example, we can use `kaylasAccount` as if it were an instance of `BankAccount`, in any situation where a `BankAccount` object would be expected.

 **Note:** This would be true even if `kaylasAccount` were instantiated as a `CheckingAccount`, but using the explicit child as parent syntax is most helpful when we want to declare objects in bulk.

 It is important to note here that the compiler just considers `kaylasAccount` to be any old `BankAccount`. But because method overriding is handled at runtime, if we call `printBalance()`, we’ll see something `CheckingAccount` specific:

 ```
Your checking account balance is $600.00
 ```

This is because at runtime, `kaylasAccount` is recognized as the `CheckingAccount` it is. However, the compiler still believes that `kaylasAccount` is just a `BankAccount`, so calling any methods unique to the child class would throw an error.

<br>

# Child Classes in Arrays and ArrayLists

Usually, when we create an array or an `ArrayList`, the list items all need to be the same type. However, with polymorphism, we can put instances of different classes that share a parent class together in an array or `ArrayList`.

For example, let’s say we have a `Monster` parent class with a few child classes: `Vampire`, `Werewolf`, and `Zombie`. We can set up an array with instances of each:

```java
Monster dracula, wolfman, zombie1;
 
dracula = new Vampire();
wolfman = new Werewolf();
zombie1 = new Zombie();
 
Monster[] monsters = {dracula, wolfman, zombie1};
```

We can even iterate through the list of items — regardless of subclass — and perform the same action with each item:

```java
for (Monster monster : monsters) {
  monster.attack();
}
```

<br>

# Child Classes in Method Parameters

Recall that, when we call a method that contains parameters, the arguments we place in our method call must match the parameter type. With polymorphism, if we use a superclass reference as a method parameter, we can call the method using subclass reference arguments.

For example, given a `ScaryStory` class, whose constructor takes in a reference to the `Monster` class:

```java
class ScaryStory {
  Monster monster;
  String setting;
 
  public ScaryStory(Monster antagonist, String place) {
    monster = antagonist;
    setting = place;
  }
 
  public void tellStory(){
    System.out.println("Once upon a time, " + monster.name + " was at " + setting + " looking to scare some mortals.");
  }
 
  public static void main(String[] args) {
    Monster dracula;
    dracula = new Vampire("Dracula");

    // A Vampire class is passed as the first arguement, even though the constructor
    // requested an object from the Monster class. This is allowed because Vampire is
    // a subclass of the Monster class.
    ScaryStory countDracula = new ScaryStory(dracula, "Dracula Castle");
    countDracula.tellStory();
  }
}
```

