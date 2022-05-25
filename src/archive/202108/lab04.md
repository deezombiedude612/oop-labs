---
template: base.html
---

# Practical 04: Arrays and ArrayLists

Arrays allow for storing a series of values within one data structure.
We will be working on implementing solutions that involve the use of arrays and ArrayList data structures in this practical.

## Tasks

### Task 1

Write a Java program that prompts for 10 integers.

1. Print all the elements of the array in a single row, separated by spaces.
2. Count and total up the negative numbers from the input.
3. Count and total up the positive numbers from the input.

### Task 2

Write a Java program that prints the index of the smallest element in an array of integers.

Sample arrays:

`[6, 33, 3, 63, 25, 1, 99]` will return index 5

`[10, -3, 55, -10, -24, 54, 0, -21, 8]` will return index 4

Randomly generate 10 numbers between 0 and 100 for the first array.
For the second array, randomly generate 10 numbers between -100 and 100.

### Task 3

Bubble sort works by swapping adjacent elements if they are not in the desired order.
This process repeats from the beginning of the array until all elements are in order.

Here are the steps for sorting an array of numbers from smallest to largest:

<span style="text-decoration: underline;">FIRST ITERATION</span>

**4** **2** 1 5 3 : The first two elements are in the wrong order (i.e., 4 > 2), so we swap them.

2 **4** **1** 5 3 : The second two elements are in the wrong order (i.e., 4 > 1) &#8594; swap.

2 1 **4** **5** 3 : These two elements are in the right order (i.e., 4 < 5) &#8594; do nothing.

2 1 4 **5** **3** : Swap.

2 1 4 3 5 : Resulting array after first iteration.

<span style="text-decoration: underline;">SECOND ITERATION</span>

**2** **1** 4 3 5 : Wrong order (i.e., 2 > 1) &#8594; swap.

1 **2** **4** 3 5 : Right order (i.e., 2 < 4) &#8594; do nothing.

1 2 **4** **3** 5 : Wrong order (i.e., 4 > 3) &#8594; swap.

1 2 3 4 5 : Resulting array after first iteration.

<span style="text-decoration: underline;">THIRD ITERATION</span>

**1** **2** 3 4 5 : Right order (i.e., 1 < 2) &#8594; do nothing.

1 **2** **3** 4 5 : Right order (i.e., 2 < 3) &#8594; do nothing.

1 2 3 4 5 : Resulting array after first iteration.

You may try out your algorithm with the following sample arrays:

1. `[6, 32, 7, 2, 99, 31, 53]`
2. `[-1, -23, -5, -75, -21, -43, -15]`
3. `[6, 21, -43, 12, 75, -32, -6]`
4. Array of 10 randomly generated numbers (between 0 and 100)

### Task 4

Suppose the weekly hours for all employees are stored in a two-dimensional array.
Each row records an employee's seven-day work hours with seven columns.
For example, the following array stores the work hours for eight employees.
Write a program that displays employees and their total hours worked.
Initialize the array with the values shown in the following table.

|            | Sun | Mon | Tues | Wed | Thur | Fri | Sat |
| ---------- | :-: | :-: | :--: | :-: | :--: | :-: | :-: |
| Employee 0 |  2  |  4  |  3   |  4  |  5   |  8  |  8  |
| Employee 1 |  7  |  3  |  4   |  3  |  3   |  4  |  4  |
| Employee 2 |  3  |  3  |  4   |  3  |  3   |  2  |  2  |
| Employee 3 |  9  |  3  |  4   |  7  |  3   |  4  |  1  |
| Employee 4 |  3  |  5  |  4   |  3  |  6   |  3  |  8  |
| Employee 5 |  3  |  4  |  4   |  6  |  3   |  4  |  4  |
| Employee 6 |  3  |  7  |  4   |  8  |  3   |  8  |  4  |
| Employee 7 |  6  |  3  |  5   |  9  |  2   |  7  |  9  |

Sample Output:

    The total working hours in a week for
    Employee 0 is 34 hours
    Employee 1 is 28 hours
    Employee 2 is 20 hours
    Employee 3 is 31 hours
    Employee 4 is 32 hours
    Employee 5 is 28 hours
    Employee 6 is 37 hours
    Employee 7 is 41 hours

!!! note

    Syntax for declaring and creating 2-dimensional arrays:

    ```
    dataType[][] variableName = new dataType[x][y];
    ```

### Task 5

Write a Java program that reads an unspecified number of scores and determines how many scores are above or equal to the average and how many scores are below the average.
Enter a negative number to signify the end of the input.
Assume that the maximum number of scores that can be input is 10.

Sample Output:

    Enter the scores (negative number to end)

    Score 1: 10
    Score 2: 10
    Score 3: 6
    Score 4: 6
    Score 5: 2
    Score 6: -1

    Results
    =======
    Average is 6.8
    Number of scores above or equal to the average is 2
    NUmber of scores below the average is 3

    Process completed.
