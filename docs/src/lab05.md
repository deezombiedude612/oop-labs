---
title: "Practical 05"
editlink: true
navbar: true
---

# Practical 05: Methods

Aside from being able to modularize code, using methods is integral to when we start covering Classes and Objects in the next session.

## Tasks

### Task 1

Write a method that computes the multiplication of the digits in an integer.
Use the following method header:

```java
public static int mulDigit (int n)
```

For exmaple, `mulDigit(234)` returns 24 (i.e., 2 &#215; 3 &#215; 4).

::: details HINT
Use the `%` operator to extract digits, and the `/` operator to remove the extracted digit.
For instance, to extract 4 from 234, use `234 % 10` (= 4).
To remove 4 from 234, use `234 / 10` (= 23).
Use a loop to repeatedly extract and remove the digit until all the digits are extracted.
Write a test program that prompts the user to enter an integer and displays the multiplication of all its digits.
:::

Write a test program that

1. prompts the user to enter an integer, then displays the result of all its digits multiplied together
2. randomly generates a number ranging between (and inclusive of) 100 and 10,000, then displays the result of all its digits multiplied together

### Task 2

Create a class called `PrimeNumber` which contains 3 methods:

1. `isPrimeNumber(int num)`<br>
   This will return **true** if `num` is prime, and **false** otherwise.
2. `getListOfPrimeNumbers(int start, int end)`<br>
   This will return the list of prime numbers between the `start` and `end` number.
3. `getDivisible(int num)`<br>
   This will return the list of divisible numbers for the provided number.

### Task 3

Write a method that converts a hexadecimal number into a decimal number.
For example,

ABCD<sub>16</sub> = A &#215; 16<sup>3</sup> + B &#215; 16<sup>2</sup> + C &#215; 16<sup>1</sup> + D &#215; 16<sup>0</sup> = 43981

You may use the following reference:

| Hexadecimal |  0  |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  |  A  |  B  |  C  |  D  |  E  |  F  |
| ----------- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| Decimal     |  0  |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11  | 12  | 13  | 14  | 15  |

Once you have completed your method, you can verify your result by calling the following function:

```java
Integer.parseInt(<number_input>, 16);
```

Test your program with the following values: 2AC, AB3F, FF99

### Task 4

Write a class that contains the following two methods:

```java
/* Convert miles to kilometers */
public static double mileToKilometer(double mile)

/* Convert kilometers to miles */
public static double kilometerToMile(double kilometer)
```

The formula for the conversion is: 1 mile = 1.609 kilometers

Write a test program that invokes these methods when necessary after prompting to enter either a value in kilometers or miles (ask for choice first).

### Task 5

Write a class that contains the following two methods:

```java
/* Convert pounds to kilograms */
public static double poundToKilogram(double pound)

/* Convert kilograms to pounds */
public static double kilogramToPound(double kilogram)
```

The formula for the conversion is:

pound = 0.453 &#215; kilograms

kilogram = 2.204 &#215; pound

Write a test program that invokes these methods when necessary after prompting to enter either a value in kilograms or pounds (ask for choice first).
