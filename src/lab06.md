---
template: base.html
---

# Practical 06: Classes and Objects (Part 1)

We will now begin to implement classes and declare them as objects in this practical session.

In procedural programming, the idea is to break down problems into required actions to be taken.
Here, one may associate solutions as verbs (i.e., to-do actions).
Previously, we only dabbled in one class file per task solution.
In those classes, we still approached our solutions in a procedural programming manner.

However, in object-oriented programming, one has to decompose problems into objects (i.e., nouns).
One must consider what objects are needed in order for the program to function.
These objects will contain attributes and methods (i.e., their own functions) to play roles in a program.

!!! note inline end

    Up to this point, you may have ensured that each task is completed within one Java class file.
    However, going forward for the next few practical exercises, your tasks will necessitate the need to create more than one Java class file per task.
    If you wish to keep each task work separate rather but not need to create new Java projects each time, consider keeping them in separate packages instead.

## Activity: Object-Oriented Thinking

### Activity 1: The `Rectangle` Class

Design a class named Rectangle to represent a rectangle.
The class should contain:

- Two `double` data fields named `width` and `height` which specify the width and height of the rectangle respectively. The default values are 1 for both width and height.
- A no-arg constructor that creates a default rectangle.
- A constructor that creates a rectangle with the specified width and height.
- A method named `getArea()` that returns the area of the rectangle.
- A method named `getPerimeter()` that returns the perimeter of the rectangle.

Draw the UML diagram for the class and then implement the class.
Write a test program that creates two `Rectangle` objects — one with a width of 4 units and height of 40 units, and the other with a width of 3.5 units and height of 35.9 units.
Display the width, height, area, and perimeter of each rectangle in this order.

??? success "Rectangle Class (Solution)"

    ```java linenums="1" title="Rectangle.java"
    public class Rectangle {
        double width;
        double height;

        public Rectangle() {
            width = 1;
            height = 1;
        }

        public Rectangle(double newWidth, double newHeight) {
            width = newWidth;
            height = newHeight;
        }

        public double getArea() {
            return width * height;
        }

        public double getPerimeter() {
            return 2 * (width + height);
        }

    }
    ```

??? success "Test Class (Solution)"

    ```java linenums="1" title="TestRectangle.java"
    public class TestRectangle {
        public static void main(String[] args) {
            Rectangle r1 = new Rectangle(4, 40);
            Rectangle r2 = new Rectangle(3.5, 35.9);

            System.out.println("RECTANGLE 1");
            System.out.println("Width: " + r1.width);
            System.out.println("Height: " + r1.height);
            System.out.println("Area: " + r1.getArea());
            System.out.println("Perimeter: " + r1.getPerimeter());

            System.out.println("\nRECTANGLE 2");
            System.out.println("Width: " + r2.width);
            System.out.println("Height: " + r2.height);
            System.out.println("Area: " + r2.getArea());
            System.out.println("Perimeter: " + r2.getPerimeter());
        }
    }
    ```

    **OUTPUT:**
    ```
    RECTANGLE 1
    Width: 4.0
    Height: 40.0
    Area: 160.0
    Perimeter: 88.0

    RECTANGLE 2
    Width: 3.5
    Height: 35.9
    Area: 125.64999999999999
    Perimeter: 78.8
    ```

### Activity 2: The `Stock` Class

Design a class named `Stock` that contains:

- A `String` data field named `symbol` for the stock's symbol.
- A `String` data field named `name` for the stock's name.
- A `double` data field named `previousClosingPrice` that stores the stock price for the previous day.
- A `double` data field named `currentPrice` that stores the stock price for the current time.
- A constructor that creates a `Stock` object with the specified symbol and name.
- A method named `getChangePercent()` that returns the percentage changed from `previousClosingPrice` to `currentPrice`.

Draw the UML diagram for the class and then implement the class.
Write a test program that creates a `Stock` object with the stock symbol **ORCL**, the name **Oracle Corporation**, and the previous closing price of **34.5**.
Set the new current price to **34.35** and display the price-change percentage.

## Tasks

### Task 1

Create a class named `Household` (save as `Household.java`) that includes a default constructor and two data fields (number of occupants and annual income).
The first data field has been created for you in the following code snippet.
And then, create a driver program (save as `TestHousehold.java`) to test the class.

```java linenums="1" hl_lines="2-4" title="Household.java"
public class Household {
   /* attributes here */
   public int numberOfOccupants;
   // declare the annual income attribute here

   /* methods here */
}
```

```java linenums="1" hl_lines="3" title="TestHousehold.java"
public class TestHousehold {
    public static void main(String[] args) {
        // enter stuff here to test your program for this task
    }
}
```

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

    ```java linenums="1" hl_lines="6-9" title="Household.java"
    public class Household {
        /* attributes here */

        /* methods here */

        // default constructor (no-arg constructor)
        public HouseHold() {
            // work here
        }
    }
    ```

2.  Create an additional overloaded constructor for the `Household` class.
    This constructor receives an integer argument and assigns the value to the occupant field.
    Change any needed statements to the driver program to ensure that the overloaded constructor works correctly.
    Save and test the changes made.

    ```java linenums="1" hl_lines="11-14" title="Household.java"
    public class Household {
        /* attributes here */

        /* methods here */

        // default constructor (no-arg constructor)
        public HouseHold() {
            /* ... */
        }

        // overloaded constructor
        public Household(int numberOfOccupants) {
            // work here
        }
    }
    ```

3.  Create another overloaded constructor for the `Household` class.
    This constructor receives two arguments, the values of which are assigned to the occupant and income fields respectively.
    Add any needed statements to the driver program to ensure that the overloaded constructor works correctly.
    Save and test the changes made.

    ```java linenums="1" hl_lines="16-19" title="Household.java"
    public class Household {
        /* attributes here */

        /* methods here */

        // default constructor (no-arg constructor)
        public HouseHold() {
            /* ... */
        }

        // overloaded constructor #1
        public Household(int numberOfOccupants) {
            /* ... */
        }

        // overloaded constructor #2
        public HouseHold(int numberOfOccupants, double annualIncome) {
            // work here
        }
    }
    ```

4.  Create a method named `calcAverageIncome()` (add it to the `Household` class) to calculate the average income for each household.
    The formula is as follows:

        Average income = annual income / number of occupants

    Add any needed statements to the driver program to ensure that the method works correctly.
    Save and test the changes made.

    ```java linenums="1" hl_lines="21-24" title="Household.java"
    public class Household {
        /* attributes here */

        /* methods here */

        // default constructor (no-arg constructor)
        public HouseHold() {
            /* ... */
        }

        // overloaded constructor #1
        public Household(int numberOfOccupants) {
            /* ... */
        }

        // overloaded constructor #2
        public HouseHold(int numberOfOccupants, double annualIncome) {
            /* ... */
        }

        // calculates average income of household
        public double calcAverageIncome() {
            // work here
        }
    }
    ```

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

1.  Add the following constructors to your `Planet` class:

    - A no-arg constructor to initialize the value of `name` to "Earth" and `travelDays` to 365.

    - A constructor with two parameters.

    Modify your test class to test the constructors you have defined.

2.  Add a `calculateAge()` method to your `Planet` class which calculates the person's age on that planet.
    Use the following formula:

        Age on the planet = (age * 365) / travelDays

    The `calculateAge()` method should receive an argument that represents the age on Earth.
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
