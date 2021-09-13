---
title: "Practical 10"
editlink: true
navbar: true
---

# Practical 10: Exception Handling

Unfortunately, we live in a society where there exist individuals who are fascinated with breaking stuff.
This is no different with programs, but this is one way on how bugs are discovered in programs.
In this practical, let's start playing the devil's advocate and do all we can to patch such problems.

Java provides Exception classes that can be used to cater for unintended occurrences.
While utilizing Exceptions are always welcome, one should try to resort to using simpler tactics whenever possible (e.g., implementing checks with if-else statements).
It is also worth noting that for some languages, utilizing exception handling is not strongly encouraged.

## Activity: Applying Exception Handling into a Program

## Tasks

### Task 1

Write a program that prompts the user to read two integers and displays their multiplication.
Your program should prompt the user to read the number again if the input is incorrect.

Example Output:

    Enter two integers: 3 a
    Incorrect input! Re-enter two integers: a 3
    Incorrect input! Re-enter two integers: 3 3
    Multiplication is 9

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

### Optional Task (Challenge Question)

Write a calculator program.
The program terminates if any operand is non-numeric.
Write a program with an exception handler that deals with non-numeric operands; then write another program without using an exception handler to achieve the same objective.
Your program should display a message that informs the user of the wrong operand type before exiting.

Example Output:

    Input:
    5 + y
    Wrong Input: y

    Input:
    4f x 5
    Wrong Input: 4f

    Input:
    30 / 6
    Output: 30 / 6 = 5
