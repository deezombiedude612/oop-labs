---
template: base.html
---

# Practical 02: Selection Statements

We will now proceed with implementing selection statements in this practical.
Selection statements in Java include the if-else statement, and the switch statement.

## Tasks

### Task 1

Write a lottery program that randomly generates a two-digit number (10-99), prompts the user to enter another two-digit number (also 10-99), and determines what the user wins according to the following rules:

- If the user input exactly matches the randomly generated lottery number, the reward is $10,000.
- If the user input has both numbers used in the generated lottery number, the reward is $3,000.
- If any one of the digits in the user input matches one of the digits used in the generated lottery number, the reward is $1,000.
- Give no reward otherwise.

### Task 2

Write a program that prompts the user to enter a year and display the Chinese zodiac animal that corresponds with the given remainder after dividing by 12:

| Remainder | Chinese Zodiac Animal | Remainder | Chinese Zodiac Animal |
| :-------: | :-------------------: | :-------: | :-------------------: |
|     0     |        Monkey         |     6     |         Tiger         |
|     1     |        Rooster        |     7     |        Rabbit         |
|     2     |          Dog          |     8     |        Dragon         |
|     3     |          Pig          |     9     |         Snake         |
|     4     |          Rat          |    10     |         Horse         |
|     5     |          Ox           |    11     |         Sheep         |

### Task 3

The Body Mass Index (BMI) is a measure of health on weight.
A person's BMI is calculated by taking the person's weight (in kilograms) divided by the person's height squared (height in meters).
Create a BMI program that takes in both a person's weight and height as values to interpret the person's BMI.
The respective BMI interpretations are as follows:

|        BMI        | Interpretation |
| :---------------: | :------------: |
|    BMI < 18.5     |  Underweight   |
| 18.5 ≤ BMI < 25.0 |     Normal     |
| 25.0 ≤ BMI < 30.0 |   Overweight   |
|    BMI ≥ 30.0     |     Obese      |

### Task 4

The personal income tax is calculated based on the filing status and taxable income.
There are four filing statuses: single filers, married filing jointly, married filing separately, and head of household.
The tax rates are as shown below.

![Task 4 Tax Rates](./images/lab02-04.png)

Create a program that prompts users to input their filing status and taxable income to calculate the required tax payment for the year.

### Task 5

Write a program to calculate the electricity bill with the rates as follows:

| Consumed Units | Rate ($) |
| :------------: | :------: |
|      1-50      |   1.15   |
|     51-100     |   2.60   |
|    101-150     |   3.55   |
|    151-200     |   4.50   |
|    201-300     |   5.90   |
|    301-400     |   6.90   |
|    401-500     |   7.90   |
|    501-1000    |   8.90   |
|     >1000      |  10.99   |

Sample Output:

    Enter Previous Month Reading: 180
    Enter Current Month Reading: 275
    Total Units Consumed: 95
    Total Bill: $174.50

??? hint

    ```
    (50 * 1.15) + (45 * 2.60)
    ```
