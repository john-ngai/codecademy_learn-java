# Section 6 - Loops

Learn Java by Codecademy

**Reference:** https://www.codecademy.com/courses/learn-java/lessons/learn-java-loops/

# Introduction to Loops

A *loop* is a programming tool that allows developers to repeat the same block of code until some condition is met.

We’ll go over three types of loops that we’ll see everywhere:

* `while` loops
* `for` loops
* for-each loops

<br>

# While Loops

## Syntax

A `while` loop looks a bit like an `if` statement:

```java
while (silliness > 10) {
  // code to run...
}
```

Like an `if` statement, the code inside a `while` loop will only run if the condition is `true`.

**Example 1** - A `while` loop:

```java
// set attempts to 0
int attempts = 0;
 
// enter loop if condition is true
while (passcode != 0524 && attempts < 4) {
 
  System.out.println("Try again.");
  passcode = getNewPasscode();
  attempts += 1;
 
  // is condition still true?
  // if so, repeat code block
}
// exit when condition is not true
```

`while` loops are extremely useful when you want to run some code until a specific change happens.

*Infinite loops* occur when the condition will never evaluate to `false`. This can cause your entire program to crash.

**Example 2** - An infinite loop:

```java
int hedgehogs = 5;

// hedgehogs remains equal to 5, which is less than 6,  so we would get an infinite loop.
while (hedgehogs < 6) {
  System.out.println("Not enough hedgehogs!");
}
```

<br>

## Incrementing While Loops

When looping through code, it’s common to use a counter (also known as an iterator) variable:

```java
// counter is initialized
int wishes = 0;
 
// conditional logic uses counter
while (wishes < 3) {
  System.out.println("Wish granted.");

  // counter is incremented
  wishes++;
}

/*
Output:
  Wish granted.
  Wish granted.
  Wish granted.
*/
```

<br>

# For Loops

## Syntax

A `for` loop header is made up of the following three parts, each separated by a semicolon:

1. The initialization of the loop control variable.
2. A boolean expression.
3. An increment or decrement statement.

The opening line might look like this:

```java
for (int i = 0; i < 5; i++) {
  // code that will run...
}
```

In a `for` loop, an initialization statement is run once in order to initialize the loop control variable. In the example above, `i` is the loop control variable.

Let’s breakdown the above example:

1. `i = 0`: `i` is initialized to `0`.

2. `i < 5`: the loop is given a boolean condition that relies on the value of `i`. The loop will continue to execute until `i < 5` is `false`.

3. `i++`: `i` will increment at the end of each loop and before the condition is re-evaluated.

**Note:** We often hear the term “iteration” in reference to loops. When we *iterate*, it just means that we are repeating the same block of code.

## Off By One Error

It’s important to be aware that, if we don’t create the correct `for` loop header, we can cause the iteration to loop one too many or one too few times; this occurrence is known as an *off by one* error.

For example, imagine we wanted to find the sum of the first ten numbers and wrote the following code:

```java
int sum = 0;

for (int i = 0; i < 10; i++) {
  sum += i;
}
```

This code would produce an incorrect value of `45`.

We skipped adding `10` to sum because our loop control variable started with a value of `0` and stopped the iteration after it had a value of `9`. We were off by one! This is fixed by changing the condition of our loop to be `i <= 10;` or `i < 11;`.

<br>

# Iterating Over Arrays and ArrayLists

One common pattern we’ll encounter as a programmer is *traversing*, or looping, through a list of data and doing something with each item. In Java, that list would be an array or `ArrayList`.

## Traversing Through Arrays

**Example 1** - Incrementing the value of each element in a `secretCode` array using a `for` loop:

```java
for (int i = 0; i < secretCode.length; i++) {
  // Increase the element's value by 1
  secretCode[i] += 1;
}
```

**Example 2** - Incrementing the value of each element in a `secretCode` array using a `while` loop:

```java
int i = 0; // initialize counter
 
while (i < secretCode.length) {
  secretCode[i] += 1;
  i++; // increment the while loop
}
```

## Traversing Through ArrayLists

**Example 1** - Incrementing the value of each element in a `secretCode` `ArrayList` using a `for` loop:

```java
for (int i = 0; i < secretCode.size(); i++) {
  // Increase the element's value by 1
  int num = secretCode.get(i);
  secretCode.set(i, num + 1);
}
```

**Example 2** - Incrementing the value of each element in a `secretCode` `ArrayList` using a `while` loop:

```java
int i = 0; // initialize counter
 
while (i < secretCode.size()) {
  int num = secretCode.get(i);
  secretCode.set(i, num + 1);
  i++; // increment the while loop
}
```

<br>

# break and continue

If we ever want to exit a loop before it finishes all its iterations or want to skip one of the iterations, we can use the `break` and `continue` keywords.

## break

The `break` keyword is used to exit, or break, a loop. Once break is executed, the loop will stop iterating. For example:

```java
for (int i = 0; i < 10; i++) {
  System.out.println(i);
  if (i == 4) {
    break;
  }
}

/*
Output:
  0
  1
  2
  3
  4
*/
```

## continue

The `continue` keyword can be placed inside of a loop if we want to skip an iteration. If `continue` is executed, the current loop iteration will immediately end, and the next iteration will begin.

For example, we can use the `continue` keyword to skip any even valued iteration:

```java
int[] numbers = {1, 2, 3, 4, 5};
 
for (int i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 == 0) {
    continue;
  }
  System.out.println(numbers[i]);
}

/*
Output:
  1
  3
  5
*/
```

## Looping Inside Methods

If the `return` keyword was executed inside a loop contained in a method, then the loop iteration would be stopped and the method/constructor would be exited.

For example, we have a method called `checkForJacket()` that takes in an array of type `String`. As soon as an element equals `"jacket"`, `return true;` is executed. This causes the loop to stop and the compiler to exit `checkForJacket()`:

```java
public static boolean checkForJacket(String[] lst) {
  for (int i = 0; i < lst.length; i++) {
    System.out.println(lst[i]);
    if (lst[i] == "jacket") {
      return true;
    }
  }
  return false;
} 
 
public static void main(String[] args) {
  String[] suitcase = {"shirt", "jacket", "pants", "socks"};   
  System.out.println(checkForJacket(suitcase));
}

/*
Output:
  shirt
  jacket
  true
*/
```

<br>

# For-Each Loops

*For-each loops*, also referred to as *enhanced loops*, allow us to directly loop through each item in a list of items (like an array or `ArrayList`) and perform some action with each item.

**Example** - for-each loop syntax:

```java
for (String inventoryItem : inventoryItems) {
  // Print element value
  System.out.println(inventoryItem);
}
```

We can read the `:` as “in”, like this: for each `inventoryItem` (which should be a `String`) in `inventoryItems`, print `inventoryItem`.

**Important:** If we try to assign a new value to the enhanced `for` loop variable, the value stored in the array or ArrayList **will not** change. This is because, for every iteration in the enhanced loop, the loop variable is assigned a **copy** of the list element, not the list element itself.

**Note:** We can name the enhanced `for` loop variable whatever we want; using the singular of a plural is just a convention. For example, we may also encounter conventions like `String word : sentence`.

<br>

# Removing Elements During Traversal

When an element is removed from an `ArrayList`, all the items that appear after the removed element will have their index value shift by negative one. We’ll have to be very careful with how we use our counter variable to avoid skipping elements.

## Removing An Element Using while

When using a `while` loop and removing elements from an `ArrayList`, we **should not** increment the while loop’s counter whenever we remove an element. We don’t need to increase the counter because all of the other elements have now shifted to the left.

**Example** - Removing all odd numbers from an `ArrayList` using a `while` loop:

```java
int i = 0; // initialize counter
 
while (i < lst.size()) {
  // if value is odd, remove value
  if (lst.get(i) % 2 != 0){
    lst.remove(i);
  } else {
    // if value is even, increment counter
    i++;
  }
}
```

## Removing An Element Using for

When using a `for` loop, we, unfortunately, must increase our loop control variable. As a workaround, we can decrease the loop control variable whenever we remove an item.

**Example** - Removing values from an `ArrayList` using a `for` loop:

```java
for (int i = 0; i < lst.size(); i++) {
  if (lst.get(i) == "value to remove"){
    // remove value from ArrayList
    lst.remove(lst.get(i));
    
    // Decrease loop control variable by 1
    i--;    
  }
}
```

**Note:** Avoid manipulating the size of an `ArrayList` when using an enhanced `for` loop. Actions like adding or removing elements from an `ArrayList` when using a for-each loop can cause a `ConcurrentModificationException` error.
