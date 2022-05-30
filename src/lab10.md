---
template: base.html
---

# Practical 10: Exception Handling

Unfortunately, we live in a tragic society where there exist individuals who are fascinated with breaking stuff, and those who would rather fight for the right to do whatever they so please.
This is no different with programs, but this is one way on how bugs are discovered in programs.
In this practical, let's start playing the devil's advocate and do all we can to patch such problems.
Who says that there is absolutely nothing that can be done to prevent their actions from affecting others?

Java provides Exception classes that can be used to cater for unintended occurrences.
While utilizing Exceptions are always welcome, one should try to resort to using simpler tactics whenever possible (e.g., implementing checks with if-else statements).
It is also worth noting that for some languages, utilizing exception handling is not strongly encouraged.

## Activity: Applying Exception Handling into a Program

Let's revisit that Staff program we just around to developing these past three practical sessions.
We'll begin with the abstract parent class `AcademicStaff.java`.

### AcademicStaff.java

`AcademicStaff.java` has attributes `fullName`, `id`, and `qualificationLevel`.
From the way we've implemented the `qualificationLevel` attribute, it can take one of 3 values: 1 (Bachelor), 2 (Master), or 3 (Doctorate).

Let's make it such that when initializing an AcademicStaff object, it throws an Exception when any other value is received for `qualificationLevel`
(not that it can now since it's abstract, but it will do the same for the subclasses).
We will now modify the mutator method for this attribute like as follows:

```java linenums="1" hl_lines="2-3"
public void setQualificationLevel(int qualificationLevel) {
    if (qualificationLevel < 1 || qualificationLevel > 3)
        throw new IllegalArgumentException("Qualification Level must be either 1, 2, or 3!");

    this.qualificationLevel = qualificationLevel;
}
```

Here, we are throwing an `IllegalArgumentExcpetion` back to the method that called it.
The `IllegalArgumentExcpetion` class is one of many exception classes that exist in Java.
This one in particular is best used here since we can regard a qualification level which is not one of the stated values (i.e., 1-3) as an illegal argument/value.

### FullTimeStaff.java

The `rank` attribute follows the same convention as with the `AcademicStaff`'s `qualificationLevel` attribute.

```java linenums="1" hl_lines="2-3"
public void setRank(int rank) {
    if (rank < 1 || rank > 3)
        throw new IllegalArgumentException("Rank must be either 1, 2, or 3!");

    this.rank = rank;
}
```

For both the `contributionHours` and `baseSalary` attributes, they are expected to contain non-negative values.
We can proceed to throw an exception each time a negative value is entered, or we can set it to 0 instead (this does not require throwing an Exception, rather to implement an if-else statement).
The choice is entirely up to you.

#### Throwing an Exception

```java linenums="1" hl_lines="2-3"
public void setContributionHours(int contributionHours) {
    if (contributionHours < 0)
        throw new IllegalArgumentException("Contribution hours cannot be negative!");

    this.contributionHours = contributionHours;
}
```

```java linenums="1" hl_lines="2-3"
public void setBaseSalary(int baseSalary) {
    if (baseSalary < 0)
        throw new IllegalArgumentException("Base salary cannot be negative!");

    this.baseSalary = baseSalary;
}
```

#### Defaulting to 0

```java linenums="1" hl_lines="2-5"
public void setContributionHours(int contributionHours) {
    if (contributionHours < 0)
        this.contributionHours = 0;
    else
        this.contributionHours = contributionHours;
}
```

```java linenums="1" hl_lines="2-3"
public void setBaseSalary(int baseSalary) {
    if(baseSalary < 0)
        this.baseSalary = 0;
    else
        this.baseSalary = baseSalary;
}
```

### PartTimeStaff.java

The same approaches to `FullTimeStaff`'s attributes can be done for `PartTimeStaff`'s `hourlyRate` and `hoursWorked` attributes.
Simply modify their mutator methods to work similarly.

Apart from these mutator methods, we can also modify the `addHoursWorked()` method such that it will not take in negative values.
In this case, reverting the `hoursWorked` value is not appropriate.
Thus, you should throw an `IllegalArgumentException` object instead in its place.

### Forcing Constructors to Use Modified Mutator Methods

Let's now modify the constructors in this class as well as the two subclasses such that they use the mutator methods by default when called.

```java linenums="1" hl_lines="8-10" title="AcademicStaff.java"
public abstract class AcademicStaff {
	private String fullName;
	private String id;
	private int qualificationLevel;

	// Constructor
	protected AcademicStaff(String fullName, String id, int qualificationLevel) {
		setFullName(fullName);
		setId(id);
		setQualificationLevel(qualificationLevel);
	}

	/* ... */
}
```

```java linenums="1" hl_lines="10-12 18-19 23 27 31 35" title="FullTimeStaff.java"
public class FullTimeStaff extends AcademicStaff {
	private int rank;
	private int contributionHours;
	private double baseSalary;

	// Constructors
	public FullTimeStaff(String fullName, String id, int qualificationLevel,
	                     int rank, int contributionHours, double baseSalary) {
		super(fullName, id, qualificationLevel);
		setRank(rank);
		setContributionHours(contributionHours);
		setBaseSalary(baseSalary);
	}

	public FullTimeStaff(String fullName, String id, int qualificationLevel,
	                     int rank, int contributionHours) {
		super(fullName, id, qualificationLevel);
		setRank(rank);
		setContributionHours(contributionHours);

		switch(this.rank) {
			case 1:
				setBaseSalary(2000);
				break;

			case 2:
				setBaseSalary(2500);
				break;

			case 3:
				setBaseSalary(3000);
				break;

			default:
				setBaseSalary(0);
		}
	}

	public FullTimeStaff(PartTimeStaff pt, int rank, int contributionHours) {
		this(pt.getFullName(), pt.getId(), pt.getQualificationLevel(), rank,
				contributionHours);
	}

    /* ... */
}
```

```java linenums="1" hl_lines="9-10 16-17" title="PartTimeStaff.java"
public class PartTimeStaff extends AcademicStaff {
	private double hourlyRate;
	private int hoursWorked;

	// Constructors
	public PartTimeStaff(String fullName, String id, int qualificationLevel,
	                     double hourlyRate, int hoursWorked) {
		super(fullName, id, qualificationLevel);
		setHourlyRate(hourlyRate);
		setHoursWorked(hoursWorked);
	}

	public PartTimeStaff(String fullName, String id, int qualificationLevel,
	                     double hourlyRate) {
		super(fullName, id, qualificationLevel);
		setHourlyRate(hourlyRate);
		setHoursWorked(0);
	}

	public PartTimeStaff(FullTimeStaff ft, double hourlyRate) {
		this(ft.getFullName(), ft.getId(), ft.getQualificationLevel(),
				hourlyRate);
	}

	/* ... */
}

```

### try-catch-finally block

We've implemented the classes such that they throw the appropriate Exception classes as and when necessary.
However, without specifying a method of catching such Exception classes, your program will not terminate gracefully.

In the driver class' `main` method, surround your code with the try-catch block as follows:

```java linenums="1" hl_lines="3-11" title="Driver.java"
public class Driver {
	public static void main(String[] args) {
		try {

            /* testing code goes here */

		} catch(IllegalArgumentException ex) {
            System.out.println(ex.getMessage());
		} catch(Exception ex) {
            ex.printStackTrace();
        }
	}
}
```

The program is now set to check for Exception objects being thrown from anything that is called from the `try` block.
Once the matching Exception object is caught, the program proceeds to run the statements from within that `catch` block.
Whatever statements yet to be run from the `try` block is skipped.

Notice that the program checks for an `IllegalArgumentException` object first before a more generic `Exception` object.
In practice, you should cater to catch specific Exception types before ending with checking for objects of the generic `Exception` class.

```java linenums="1" hl_lines="11-13" title="Driver.java"
public class Driver {
	public static void main(String[] args) {
		try {

            /* testing code goes here */

		} catch(IllegalArgumentException ex) {
            System.out.println(ex.getMessage());
		} catch(Exception ex) {
            ex.printStackTrace();
		} finally {
            System.out.println("End of Staff program");
        }
	}
}
```

Regardless of whether an Exception is caught, if a `finally` block exists, all statements from this block is run.
Statements in the `finally` block can be used to close resources (e.g., for writing to files) or display specific messages (e.g., to signal the end of the program).

Now, go bonkers and see if your attempts at securing your program a little better worked!

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

```java linenums="1"
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
