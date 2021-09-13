---
title: "Practical 11"
editlink: true
navbar: true
---

# Practical 11: File I/O

A useful application of classes and exception handling in Java is File I/O.
In this practical activity, we will utilize classes specifically meant to carry out file I/O with text files.

## Tasks

### Task 1

Write a program that reads from Exercise1.txt and counts the number of characters, words, and lines in a file.
Words are separated by whitespace characters.

[Exercise1.txt](./lab11-props/Exercise1.txt)

### Task 2

Write a program that meets the following requirements:

- Create an array with 100 randomly chosen integers.
- Prompt the user to enter the array index, then display the corresponding element value.
  If the specified index is out of bounds, display the message "Index out of bounds".

Example Output:

    Enter an index: 101
    Index out of bounds

    Enter an index: 55
    The element is 7313

    Enter an index: 108
    Index out of bounds

### Task 3

Write a class named `TestScores`.
The class constructor should accept any array of test scores as its argument.
The class should have a method that returns the average of the test scores.
If any test score in the array is negative or greater than 100 then the class should throw an IllegialArugumentException with the specified detail message to its caller.
Demonstrate the usage of the class in a test program.

### Task 4

Write a program that uses the following method to solve equations specified by the user.

```java
/**
 * Returns the larger of the two roots of
 * the quadratic equation A*x*x + B*x + C = 0.
 * (Throws an exception if A == 0 or B*B-4*A*C < 0.)
 */
public static double root(double A, double B, double C) throws IllegalArgumentException {
	if (A == 0) {
		throw new IllegalArgumentException("A can't be zero.");
	} else {
		double disc = B * B - 4 * A * C;

		if (disc < 0)
			throw new IllegalArgumentException("Discriminant < zero.");

		return (-B + Math.sqrt(disc)) / (2 * A);
	}
}
```

Your program should allow the user to specify values for `A`, `B`, and `C`.
It should call the method to compute a solution of the equation.
If no error occurs, it should print the root.
However, if an error occurs, your program should catch that error and print an error message.
After processing one equation, the program should ask whether the user wants to enter another equation.
The program should continue until the user answers no.
