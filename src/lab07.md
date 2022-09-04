---
template: base.html
---

# Practical 07: Classes and Objects (Part 2)

Continuing off where we left off in the previous practical, we will now implement a form of encapsulation into our program.

## Tasks

### Task 1

Modify your `Planet` class (from Practical 06) by making its data members _private_ and adding the relevant `get` and `set` methods.
Modify your test class accordingly to test the `get` and `set` methods that you have written.

1.  Modify the driver program to include an array of `Planet` objects.
    Use the enhanced `for` loop to display the age corresponding to each `Planet` object stored in the array.

2.  Modify the `Planet` class by using the `this` keyword to refer to the data member(s) and constructor (if possible).

### Task 2

Create a class based on the following class diagram:

<!-- ```mermaid
classDiagram
	class House {
		- type: String
		- zone: char
		- price: double
		- numberOfBedrooms: int
		- freehold: boolean
		+ House()
		+ House(type: String, price: double, numberOfBedrooms: int)
		+ House(type: String, zone: char, price: double, numberOfBedrooms: int, freehold: boolean)
		+ getters and setters
		+ toString(): String
	}
``` -->

![Task 2 Class Diagram](./images/lab07-02.png)

Notes:

- Initialize the value of `type` to “Apartment”, `zone` to ‘A’, `price` to 68000.00, `numberOfBedrooms` to 3 and `freehold` to `false` for no-arg constructor.
- Use the `toString()` method to print out all house details.

1. Create a driver program for the class you just created to test all the available constructors and methods.

   - Create three house objects.
   - Create an array to store the three house objects.

2. Modify the `House` class by using the `this` keyword to refer to the data member(s) and constructor (if possible).

### Task 3

Consider the following information:

| **Mickey Cake House**                                                                                               |
| ------------------------------------------------------------------------------------------------------------------- |
| Flavors:<br> 1. Chocolate Moist <br> 2. Strawberry <br> 3. Blueberry <br> 4. Cheesy Cake <br> 5. American Chocolate |
| Price List:<br> 1(kg) = RM 25.50<br>2(kg) = RM 50.00<br>3(kg) = RM 75.00                                            |

#### Part 1

Create a class named `Bakery` to represent a cake ordering system.
For each cake ordering system, you would need to store details about the _flavors_ (a string), _weight_ (a string) and _quantity_ ordered.

- Provide `get` and `set` methods for each data field.
  For each `set` method's parameter, **_use the same identifier as the corresponding data field_** (this would require the use of the `this` keyword to access the object's data field within the `set` method).

- Provide 2 constructors:

      - A three-parameter constructor.
      - A no-arg constructor which initializes the respective data fields to **"Chocolate Moist"**, **"1(kg)"** and **1** unit.
      	This constructor should invoke the three parameters constructor.

- Include a `toString()` method to print out all the cake ordering details.
- Create a driver program to test all the available constructors.

#### Part 2

Add the following method to your `Bakery` class from Part 1 to return the unit price:

```java
public double getPrice()
```

**NOTE:**
The unit price is dependent on the weight of the cake.
Remember to take class design into consideration and implement any necessary constructs to ensure the maintainability of your class.
Modify the driver program to test the `getPrice()` method.

#### Part 3

**Mickey Cake House** requires an application with the following sample dialog:

```
Enter how many types of cake you would like to order >> 2

Flavor
	1. Chocolate Moist
	2. Strawberry
	3. Blueberry
	4. Cheesy Cake
	5. American Chocolate

Price List
	(1)kg = RM25.50
	(2)kg = RM50.00
	(3)kg = RM75.00

Bakery Item 1
--------------
Enter your choice of cake flavor (1 - 5) >> 1
Enter the weight of cake (1 - 1kg, 2 - 2kg and 3 - 3kg) >> 2
Enter quantity ordered >> 2

Bakery Item 2
--------------
Enter your choice of cake flavor (1 - 5) >> 4
Enter the weight of cake (1 - 1kg, 2 - 2kg and 3 - 3kg) >> 1
Enter quantity ordered >> 3

Order Details:
----------------
No 	Cake Flavor       Weight    Unit Price (RM)   Quantity   Total Price (RM)
--  --------------   --------   ---------------   --------   ----------------
1   Chocolate Moist    2kg          50.00             2            100.00
2   Cheesy Cake        1kg          25.50             3             76.50
-----------------------------------------------------------------------------
                                                  Grand Total:     176.50
```

With reference to the above requirement, identify and make necessary additions/changes to your `Bakery` class and create the required application program.

Once again, remember to take object-oriented design issues into consideration and implement the necessary constructs to ensure the maintainability of your class.
