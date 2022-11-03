---
template: base.html
---

# Practical 12: File I/O

A useful application of classes and exception handling in Java is File I/O.
In this practical activity, we will utilize classes specifically meant to carry out file I/O with text files.

## Tasks

### Task 1

Write a program that reads from `Exercise1.txt` and counts the number of characters, words, and lines in a file.
Words are separated by whitespace characters.

Download text file here: [Exercise1.txt](./props/Exercise1.txt)

### Task 2

Suppose that a text file `Exercise2.txt` contains an unspecified number of scores separated by blanks.
Write a program that prompts the user to enter the file, reads the scores from the file, and displays their total and average.

Download text file here: [Exercise2.txt](./props/Exercise2.txt)

### Task 3

Write a program that creates a file named `Exercise3.txt` if it does not already exist.
Write 100 randomly generated integers into this file using text I/O.
Integers are to be separated by spaces in the file.
Read the data back from the file and display the data in increasing order.

### Task 4

Write a program that prompts the user to enter a file name and displays the occurrences of each letter in the file.
Letters are case-insensitive.
Here is a sample run:

    Enter file name: Exercise1.txt
    The occurrence of A's is 22
    The occurrence of B's is 6
    The occurrence of C's is 4
    The occurrence of D's is 6
    The occurrence of E's is 28
    The occurrence of F's is 4
    The occurrence of G's is 1
    The occurrence of H's is 3
    The occurrence of I's is 5
    The occurrence of J's is 14
    The occurrence of K's is 2
    The occurrence of L's is 7
    The occurrence of M's is 6
    The occurrence of N's is 4
    The occurrence of O's is 7
    The occurrence of P's is 4
    The occurrence of Q's is 0
    The occurrence of R's is 15
    The occurrence of S's is 16
    The occurrence of T's is 5
    The occurrence of U's is 6
    The occurrence of V's is 6
    The occurrence of W's is 1
    The occurrence of X's is 0
    The occurrence of Y's is 7
    The occurrence of Z's is 0

### Task 5

Suppose that the text file on the Web [http://liveexample.pearsoncmg.com/data/Scores.txt](http://liveexample.pearsoncmg.com/data/Scores.txt) contains an unspecified number of scores.
Write a program that reads the scores from the file and displays their total and average.
Scores are separated by blanks.

## Challenge Tasks

### Challenge Task 1

#### Part 1

Create a data file with 1,000 lines.
Each line in the file consists of a faculty member's first name, last name, rank, and salary.
The faculty member's first name and last name for the $i$th line are FirstName$i$ and LastName$i$.
The rank is randomly generated as assistant, associate, and full.
The salary is randomly generated as a number with two digits after the decimal point.
The salary for an assistant professor should be in the range from 50,000 to 80,000, for associate professor from 60,000 to 110,000, and for full professor from 75,000 to 130,000.
Save the file in `Salary.txt`.

Here are some sample data:

```
FirstName1 LastName1 assistant 60055.95
FirstName2 LastName2 associate 81112.45
...
FirstName1000 LastName1000 full 92255.21
```

#### Part 2

Using the newly generated `Salary.txt` from Part 1, write a program to display the total salary for assistant professors, associate professors, full professors, and faculty, respectively, and display the average salary for assistant professors, associate professors, full professors, and faculty, respectively.

#### Part 3

A university posts its employees' salaries at [http://liveexample.pearsoncmg.com/data/Salary.txt](http://liveexample.pearsoncmg.com/data/Salary.txt).
Each line in the file consists of a faculty member's first name, last name, rank, and salary (see Part 1).

Using this online file, write a program to display the total salary for assistant professors, associate professors, full professors, and faculty, respectively, and display the average salary for assistant professors, associate professors, full professors, and faculty, respectively.

### Challenge Task 2

#### Part 1

The popularity ranking of baby names from years 2001 to 2010 is downloaded from [`www.ssa.gov/oact/babynames`](https://www.ssa.gov/oact/babynames) and stored in files named `babynameranking2001.txt`, `babynameranking2002.txt`, ... , `babynameranking2010.txt`.
You can download these files using the URL such as [http://liveexample.pearsoncmg.com/data/babynamesranking2001.txt](http://liveexample.pearsoncmg.com/data/babynamesranking2001.txt).
Each file contains 1,000 lines.
Each line contains a ranking, a boy's name, number for the boy's name, a girl's name, and number for the girl's name.
For example, the first two lines in the file `babynameranking2010.txt` are as follows:

```
1 	Jacob	21875 	Isabella 	22731
2 	Ethan	17866 	Sophia 	20477
```

Therefore, the boy's name Jacob and girl's name Isabella are ranked #1 and the boy's name Ethan and girl's name Sophia are ranked #2; 21,875 boys are named Jacob, and 22,731 girls are named Isabella.
Write a program that prompts the user to enter the year, gender, followed by a name, and displays the ranking of the name for the year.
Your program should read the data directly from the Web. Here are some sample runs:

```
Enter the year: 2010
Enter the gender: M
Enter the name: Javier
Javier is ranked #190 in year 2010
```

```
Enter the year: 2010
Enter the gender: F
Enter the name: ABC
The name ABC is not ranked in year 2010
```

#### Part 2

Write a program that uses the files described in Part 1 and displays a ranking summary table for the first five girl's and boy's names as follows:

```
Year Rank 1    Rank 2    Rank 3    Rank 4    Rank 5    Rank 6   Rank 7    Rank 8    Rank 9    Rank 10
2010 Isabella  Sophia    Emma      Olivia    Ava       Jacob    Ethan     Michael   Jayden    William
2009 Isabella  Emma      Olivia    Sophia    Ava       Jacob    Ethan     Michael   Alexander William
2008 Emma      Isabella  Emily     Olivia    Ava       Jacob    Michael   Ethan     Joshua    Daniel
2007 Emily     Isabella  Emma      Ava       Madison   Jacob    Michael   Ethan     Joshua    Daniel
2006 Emily     Emma      Madison   Isabella  Ava       Jacob    Michael   Joshua    Ethan     Matthew
2005 Emily     Emma      Madison   Abigail   Olivia    Jacob    Michael   Joshua    Matthew   Ethan
2004 Emily     Emma      Madison   Olivia    Hannah    Jacob    Michael   Joshua    Matthew   Ethan
2003 Emily     Emma      Madison   Hannah    Olivia    Jacob    Michael   Joshua    Matthew   Andrew
2002 Emily     Madison   Hannah    Emma      Alexis    Jacob    Michael   Joshua    Matthew   Ethan
2001 Emily     Madison   Hannah    Ashley    Alexis    Jacob    Michael   Matthew   Joshua    Christopher
```
