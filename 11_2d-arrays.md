# Section 11 - 2D Arrays

Learn Java by Codecademy

**Reference:** https://www.codecademy.com/courses/learn-java/lessons/2-d-arrays-java/

# Introduction to 2D Arrays

An array of arrays are called 2D arrays. We can logically view them as a two-dimensional matrix of values containing both rows and columns:

```java
[
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]
```

We can also have 2D arrays which are not rectangular in shape. These are called jagged arrays:

```java
[
  ['a', 'b', 'c', 'd'],
  ['e', 'f'],
  ['g', 'h', 'i', 'j'],
  ['k']
]
```

Why use 2D arrays?

* Useful for situations where you need to store and organize data by rows and columns. For example, exporting data to be used in a spreadsheet.
* Multiple arrays can be condensed down to a single variable.
* Data mapping for games such as tic-tac-toe, where state can be represented by using a 3x3 2D array.

**Note:** One downside of 2D arrays is that, one initialized, no new rows or columns can be added or removed without copying the data to a newly initialized 2D array. This is because the length of arrays in Java are immutable (unable to be changed after creation).

