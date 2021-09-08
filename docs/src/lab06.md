---
title: "Practical 06"
editlink: true
navbar: true
---

# Practical 06: Classes and Objects

We will now begin to implement classes in this practical session.

## Tasks

### Task 1

Create a class named `Household` (save as `Household.java`) that includes a default constructor and two data fields (number of occupants and annual income).
And then, create a driver program (save as `TestHousehold.java`) to test the class.

Sample output for the driver program:

    Household 1
    ***********
    Number of occupants: 0
    Annual Income: .00

    Values have been modified
    Number of occupants: 6
    Annual Income: 25,000.00

1.  Modify the default constructor for the `Household` class to set the occupants field to 1 and annual income field to 0.
    Then, run the driver program again.

2.  Create an additional overloaded constructor for the `Household` class.
    This constructor receives an integer argument and assigns the value to the occupant field.
    Change any needed statements to the driver program to ensure that the overloaded constructor works correctly.
    Save and test the changes made.

3.  Create a third overloaded constructor for the `Household` class.
    This constructor receives two arguments, the values of which are assigned to the occupant and income fields respectively.
    Add any needed statements to the driver program to ensure that the overloaded constructor works correctly.
    Save and test the changes made.

4.  Create a method named `calcAverageIncome()` (add it to the `Household` class) to calculate the average income for each household.
    The formula is as follows:

        Average income = annual income / number of occupants

    Add any needed statements to the driver program to ensure that the method works correctly.
    Save and test the changes made.

### Task 2

Define a class named `Planet`, which contains two instance variables that store the name of the planet (`name`) and the number of days the planet takes to travel around the Sun (`travelDays`).
Write a method `printPlanet()` which displays the planet's details.
In addition, write a test class to test your `Planet` class.

Sample output for the driver program:

    Enter the planet name: Earth
    Enter the travel days: 365
    -----------------------------
    Planet Name: Earth
    Travel Days: 365

1.  Add a `calculateAge()` method to yuor `Planet` class which calculates the person's age on that planet.
    Use the following formula:

        Age on the planet = (age * 365) / travelDays

    The `calculateAverage()` method should receive an argument that represents the age on Earth.
    Modify your test class to obtain user input on their age on Earth and test your `calculateAge()` method.

    | Planet  | Travel Days |
    | :-----: | :---------: |
    |  Venus  |     255     |
    | Mercury |     88      |
    | Jupiter |    4380     |
    | Saturn  |    10767    |

    Sample output for driver program:

        Enter your age on Earth: 20
        Enter the planet name: Venus
        Enter the travel days for Venus: 255
        -------------------------------------
        Planet Name: Venus
        Travel Days: 255
        Age on Venus: 28

2.  Add the following constructors to your `Planet` class:

    - A no-arg constructor to initialize the value of `name` to "Earth" and `travelDays` to 365.

    - A constructor with two parameters.

    Modify your test class to test the constructors you have defined.
