---
template: base.html
---

# Practical 03: Loop Statements

Loop structures make up the remaining part of program control structures.
We will be implementing loop structures (i.e., for loop, while loop, do-while loop) in this practical.

## Activity: for Loops vs. while Loops vs. do-while Loops

The following shows a for loop which iterates from 0 to 7, adding each iterated number into a variable called `sum`.

```java
int sum = 0;
for(int i = 0; i <= 7; i++) {
	sum = sum + i;
}
```

1. Add a line within the loop to print out the value of `sum` during each iteration.

2. Convert the given for loop into a while loop and do-while loop. Is there a difference in terms of output between these two loop types?

3. Convert the following for loop into a while loop and do-while loop. Is there a difference in terms of output between these two loop types?

```java
int sum = 0;
for(int i = 7; i < 7; i++) {
	sum = sum + i;
	System.out.println("Value of sum: " + sum);
}
```

## Tasks

### Task 1

Suppose that the tuition fees for a university program is $10,000 this year.
It is expected that the tuition fees increase by 7% per year.
Write a program that will estimate how long (in years) it will take for the tuition fees amount to be double of this year's amount.

### Task 2

Every day, a weather station receives 5 temperatures expressed in degrees Farenheit.
Write a program that will accept 5 Farenheit temperatures, and display the temperature expressed in Celsius on screen.
After 5 temperatures have been processed, output the message "All Temperatures Processed".

Conversion Formula:

    Celsius = (Farenheit - 32) * 5 / 9

Sample Output:

    Farenheit Temperature #1: 67
    67.00 degrees Farenheit is 19.44 degrees Celsius.

    Farenheit Temperature #2: 89
    89.00 degrees Farenheit is 31.67 degrees Celsius.

    Farenheit Temperature #3: 34
    67.00 degrees Farenheit is 1.11 degrees Celsius.

    Farenheit Temperature #2: 67
    89.00 degrees Farenheit is 19.44 degrees Celsius.

    Farenheit Temperature #5: 34
    89.00 degrees Farenheit is 1.1 degrees Celsius.

    All Temperatures Processed

### Task 3

Write a program that prompts the user to enter a 3-digit integer and determines whether it is a palindrome integer.
An integer is a palindrome if it reads the same from right to left and left to right.
A negative integer is treated the same as a positive integer.

Here are sample runs of this program:

![Task 3 Output](./images/lab03-03.png)

### Task 4

Write a program that displays the first 50 prime numbers in five lines, each of which contains 10 numbers.
An integer greater than 1 is prime if its only positive divisor is 1 or itself.
For example, 2, 3, 5 and 7 are prime numbers, but 4, 6, 8 and 9 are not.

??? hint

    - For each number (2, 3, 4, ...), determine whether a given number is prime.
    	The shortcut is to see if the current number is divsible by any number up to half its value.
    	Once a prime number is found, print out the prime number followed by a space.

    	```java
    	// ...
    	for(int divisor = 2; divisor < (iter / 2); divisor++) {	// shortcut is in here
    		// if current number in iteration is divisible by divisor that's not 1 or the same number as itself
    		if(iter % divisor == 0) {
    			isPrime = false;
    			break;
    		}
    	}
    	// ...
    	```

    - Have a counter value that counts up to 50 each time a prime number is found.
    	When the counter hits a multiple of 10, print a newline character.
    	When the counter value hits 50, stop the program.

### Task 5

Write a program that reads an integer between 0 and 1000 and adds all the digits in the integer.
For example, if an integer is 932, the sum of all digits is 14.

Sample output:

    Enter a number between 0 and 1000: 999
    The sum of digits is 27.

??? hint

    Use the `%` operator to extract digits and use the `/` operator to remove the extracted digit.
    For instance, `932 % 10 = 2` and `932 / 10 = 93`.

### Task 6

Construct a calculator program that takes in 2 integer variables and performs one of the following mathematical operations by choice: addition, subtraction, multiplication, division, and modulo (the remainder function).
Include a selection menu to prompt the user to select the desired mathematical operation.
