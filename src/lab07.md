---
template: base.html
---

# Practical 07: Inheritance

Inheritance is one of the key concepts in object-oriented programming.
With it, one can group similar elements (i.e., attributes and/or methods) of a group of classes and stash them in a superclass/parent class.
The separate classes (now subclasses/child classes) will inherit these similar elements while having their own unique elements that make them different from the other fellow subclasses.

## Activity: Implementing "IS-A" Relationships

Inheritance defines relationships between classes, the "IS-A" relationship type in particular.

### Illustration Example

To illustrate this, let's compare two different groups of academic staff in Taylor's College, namely the full-time staff and part-time staff.
Here, we are implying the following:

- A full-time academic staff member "**IS-A**" academic staff.
- A part-time academic staff member "**IS-A**" academic staff.

Ignore the grammatical error, the idea's to show relations between these superclass and subclasses. 😝

On a base level, every academic staff has common attributes including:

- full name (`fullName`)
- staff ID (`id`)
- qualification level (assume 1 stands for Bachelor, 2 stands for Masters, and 3 stands for PhD) (`qualificationLevel`)

Now let's compare some differences between the two types of staff:

- Full time academic staff can have two types of rankings: Lecturer, Senior Lecturer, Head of Department.
  Let's assume 1 stands for the Lecturer rank, and 2 stands for Senior Lecturer, and 3 stands for Head of Department.
  We will call this value `rank`.

  Part-time academic staff do not have a ranking to climb.

- Full-time academic staff are required to contribute hours either into the research field or undergo trainings.
  For now, let's assume the hours spent on these duties stack together with each other.
  We will call this value `contributionHours`.

  Let's also assume that part-time academic staff, on the other hand, are not expected to offer such contributions to the College.

- Part-time staff work on an hourly wage rate (`hourlyRate`).
  The salary amount paid to part-time staff is dependent on the product of their hourly wage rate and the number of hours worked.

  Full-time staff, on the other hand, are paid a baseline salary amount (`baseSalary`), plus any bonus received.

### Implementing the Idea

#### AcademicStaff.java

We begin by implementing the superclass first; name it `AcademicStaff`.

Let's assume that the `AcademicStaff` class also has 3 methods: `toString()`, `printStaff()` and `calculateSalary()`.
For now, we will say that `calculateSalary()` will immediately return 0 from a generic AcademicStaff object.
We will also implement `toString()` as a method that returns a String - the reason for this will be explained when we touch on Polymorphism next week.

```java linenums="1" title="AcademicStaff.java"
public class AcademicStaff {
	private String fullName;
	private String id;
	private int qualificationLevel;

	// Constructor
	public AcademicStaff(String fullName, String id, int qualificationLevel) {
		this.fullName = fullName;
		this.id = id;
		this.qualificationLevel;
	}

	// Accessor and Mutator Methods
	public String getFullName() {
		return fullName;
	}
	public String getId() {
		return id;
	}
	public int getQualificationLevel() {
		return qualificationLevel;
	}

	public void setFullName(String fullName) {
		this.fullName = fullName;
	}
	public void setId(String id) {
		this.id = id;
	}
	public void setQualificationLevel(int qualificationLevel) {
		this.qualificationLevel = qualificationLevel;
	}

	public String toString() {
		String qualification = "";

		switch(qualificationLevel) {
			case 1:
				qualification = "Bachelor";
				break;

			case 2:
				qualification = "Master";
				break;

			case 3:
				qualification = "Doctorate";
				break;

			default:
		}

		return "Full Name: " + fullName
				+ "\nStaff ID: " + id
				+ "\nQualification Type: " + qualification;
	}

	public void printStaff() {
		System.out.println(this.toString());
	}

	public double calculateSalary() {
		return 0;
	}
}
```

We will now implement the subclasses next.

#### FullTimeStaff.java

<!-- Let's assume that the `toString()` method for both -->

We've already established the fact that full-time staff's salary is equal to the base salary + bonus for the month.
Let's assume that the `FullTimeStaff` class has a specific method that is used during the calculation of the salary such that the bonus depends on the amount of contribution hours put in.
Specifically, assume

<div class="text-center">
Bonus Received = $ (Number of contribution hours &#215; 100)
</div>

We will call this method `getBonus()`.

```java linenums="1" title="FullTimeStaff.java"
public class FullTimeStaff extends AcademicStaff {
	private int rank;
	private int contributionHours;
	private double baseSalary;

	// Constructor
	public FullTimeStaff(String fullName, String id, int qualificationLevel,
	                     int rank, int contributionHours, double baseSalary) {
		// calls the superclass' constructor
		super(fullName, id, qualificationLevel);

		this.rank = rank;
		this.contributionHours = contributionHours;
		this.baseSalary = baseSalary;
	}

	// Accessor and Mutator Methods
	public int getRank() { return rank; }
	public int getContributionHours() { return contributionHours; }
	public double getBaseSalary() { return baseSalary; }

	public void setRank(int rank) { this.rank = rank; }
	public void setContributionHours(int contributionHours) {
		this.contributionHours = contributionHours;
	}
	public void setBaseSalary(double baseSalary) {
		this.baseSalary = baseSalary;
	}

	// Determines bonus amount
	public double getBonus() { return contributionHours * 100; }
}
```

Recall that in order for a subclass to be able to call a method or constructor belonging to the superclass, you will need to use the `super` keyword.

#### PartTimeStaff.java

There are also some specifics for the part-time staff.
Let's assume that one may add hours the number of hours worked in addition to the number of hours already being worked on.
We'll name this method `addHoursWorked()`, which takes in one parameter value called `additionalHours`.

```java linenums="1" title="PartTimeStaff.java"
public class PartTimeStaff extends AcademicStaff {
	private double hourlyRate;
	private int hoursWorked;

	// Constructor
	public PartTimeStaff(String fullName, String id, int qualificationLevel,
	                     double hourlyRate, int hoursWorked) {
		// calls the superclass' constructor
		super(fullName, id, qualificationLevel);

		this.hourlyRate = hourlyRate;
		this.hoursWorked = hoursWorked;
	}

	// Accessor and Mutator Methods
	public double getHourlyRate() { return hourlyRate; }
	public int getHoursWorked() { return hoursWorked; }

	public void setHourlyRate(double hourlyRate) {
		this.hourlyRate = hourlyRate;
	}
	public void setHoursWorked(int hoursWorked) {
		this.hoursWorked = hoursWorked;
	}

	// Add hours worked
	public void addHoursWorked(int additionalHours) {
		this.hoursWorked += additionalHours;
	}
}
```

#### Driver Program

Let's create a separate class acting as the driver class which will contain the main method.

We can create objects of each subclass like as follows:

```java linenums="1" title="Driver.java"
public class Driver {
	public static void main(String[] args) {
		FullTimeStaff staff1 = new FullTimeStaff("Horace Diaz", "ABC123", 3, 3, 10, 3000);
		System.out.println(staff1.toString());

		System.out.println("\n");

		PartTimeStaff staff2 = new PartTimeStaff("Ivan Lam", "XYZ787", 2, 125, 20);
		System.out.println(staff2.toString());

		System.out.println("(Staff2) Hours worked: " + staff2.getHoursWorked());
		staff2.addHoursWorked(5);
		System.out.println("(Staff2) Hours worked: " + staff2.getHoursWorked());
	}
}
```

At the end of this activity, you should be able to implement inheritance in your program.
However, we are not done with this program just yet.
There are still the calculation of salary still displaying 0 if the respective method is called, and each of the subclass' `toString()` methods does not show any difference.

Output:

    Full Name: Horace Diaz
    Staff ID: ABC123
    Qualification Type: Doctorate

    Full Name: Ivan Lam
    Staff ID: XYZ787
    Qualification Type: Master
    (Staff2) Hours worked: 20
    (Staff2) Hours worked: 25

We will get into those during the next practical.
