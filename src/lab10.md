---
template: base.html
---

# Practical 10: Abstract Classes and Interfaces

If you look into the hierarchy of classes in Java, you may find that you are not able to create objects out of certain superclasses.
This is often because having objects based on the structure of such superclasses don't make sense.
In such cases like these, we often keep these classes (and sometimes some of their methods as well) as abstract.

## Activity: Implementing an Abstract Class and Abstract Methods

Looking back at the program we just went through for the past two weeks, it is not very useful to have objects of just the `Employee` class.
We can change it into an abstract class by adding the `abstract` keyword in the class declaration like as follows:

```java linenums="1" hl_lines="1 7" title="AcademicStaff.java"
public abstract class AcademicStaff {
	private String fullName;
	private String id;
	private int qualificationLevel;

	// Constructor
	protected AcademicStaff(String fullName, String id, int qualificationLevel) {
		this.fullName = fullName;
		this.id = id;
		this.qualificationLevel;
	}

	/* ... */

	public double calculateSalary() {
		return 0;
	}
}
```

Here, we also modified the constructor declaration to use the `protected` keyword instead of the `public` keyword.
It barely makes a difference for the time being, but it does ensure that it cannot be invoked unless from a linked subclass.

Note that in this class, the `calculateSalary()` method is also not useful.
Apart from creating abstract classes, the `abstract` keyword can be used to create abstract methods as and when necessary.

```java linenums="1" hl_lines="15" title="AcademicStaff.java"
protected abstract class AcademicStaff {
	private String fullName;
	private String id;
	private int qualificationLevel;

	// Constructor
	protected AcademicStaff(String fullName, String id, int qualificationLevel) {
		this.fullName = fullName;
		this.id = id;
		this.qualificationLevel;
	}

	/* ... */

	public abstract double calculateSalary();
}
```

Abstract methods can still be overridden by subclasses.
However, the visibility modifier of such declarations cannot be more private than that implemented in the superclass.
In this case, you are not allowed to override the `calculateSalary()` method with any other visibility modifier apart from `public`.
However, if the declaration here in the superclass is `protected` for example, subclasses can use the same visibility modifier or use a less private one like `public`.

```java linenums="1" hl_lines="15" title="AcademicStaff.java"
protected abstract class AcademicStaff {
	private String fullName;
	private String id;
	private int qualificationLevel;

	// Constructor
	protected AcademicStaff(String fullName, String id, int qualificationLevel) {
		this.fullName = fullName;
		this.id = id;
		this.qualificationLevel;
	}

	/* ... */

	protected abstract double calculateSalary();
}
```

## Implementing a Simple Interface

Let's create an interface class named `Manners`.
We will only implement it in the `AcademicStaff` class, but the methods introduced from the `Manners` interface will be reflected on the related subclasses.
This interface will have one method called `introduce()`, but there is no restriction as to how many methods are introduced here.

```java title="Manners.java"
public interface Manners {
	void introduce();
}
```

In order to introduce the use of this interface in the `AcademicStaff` class, introduce it using the `implements` keyword like as follows:

```java linenums="1" hl_lines="1" title="AcademicStaff.java"
public class AcademicStaff implements Manners {
	/* ... */
}
```

!!! note

    The usage of the `implements` keyword can be used alongside the `extends` keyword, should an interface ever need to be implemented on a subclass.

When implementing an interface, one would require the method to be implemented.
In the `AcademicStaff` class, assume that the `introduce()` prints out a greeting statement.

```java linenums="1" hl_lines="4-6" title="AcademicStaff.java"
public class AcademicStaff implements Manners {
	/* ... */

	public void introduce() {
		System.out.println("Hi, I'm " + fullName + "!");
	}
}
```

### Optional Activity

How would you implement this interface in the subclasses should you want the `introduce()` method to act differently based on which subclass it is being called from?

## Task

In this practical task, you will build simple programs using abstract classes.
You will also learn how to add polymorphic behavior to the program using abstract methods.

### Product.java

The skeleton code for `Product.java` is given below.
The `Product` class is an abstract class that has an abstract method called `computeSalePrice()`.

```java linenums="1" hl_lines="1 10-11" title="Product.java"
// Product class is now an abstract class
public abstract class Product {
	private double regularPrice;

	// Creates a new instance of Product
	public Product(double regularPrice) {
		this.regularPrice = regularPrice;
	}

	// computeSalesPrice() is now an abstract method
	public abstract double computeSalePrice();

	public double getRegularPrice() { return regularPrice; }

	public void setRegularPrice(double regularPrice) {
		this.regularPrice = regularPrice;
	}
}
```

### Electronics.java

The `Electronics` class itself is an abstract class because it does not provide implementation of the `computeSalePrice()` abstract method.

```java linenums="1" hl_lines="1-4" title="Electronics.java"
/**
 * Electronics class is now an abstract class because it does not provide
 * implementation of the computeSalePrice() abstract method.
 */
public abstract class Electronics extends Product {
	private String manufacturer;

	// Creates a new instance of Electronics
	public Electronics(double regularPrice, String manufacturer) {
		super(regularPrice);
		this.manufacturer = manufacturer;
	}

	public String getManufacturer() { return manufacturer; }

	public void setManufacturer(String manufacturer) {
		this.manufacturer = manufacturer;
	}
}
```

1.  Write `MP3Player.java`.
    The `MP3Player` class extends the `Electronics` class.
    The `MP3Player` class should implement the `computeSalePrice()` method with the following statement:

    ```java
    return super.getRegularPrice() * 0.9;
    ```

    Note:
    In addition to the implementation of the abstract method, you also need to include a constructor and a `String` instance variable called `color`.

2.  Write `TV.java`.
    The `TV` class extends the `Electronics` abstract class.
    The `TV` class should also implement the `computeSalePrice()` method, but with the following statement:

    ```java
    return super.getRegularPrice() * 0.8;
    ```

    Note:
    In addition to the implementation of the abstract method, you also need to include a constructor and an `int` instance variable called `quantity`.

3.  Complete `Book.java`.
    The `Book` class extends the `Product` class.
    The `Book` class should also implement the `computeSalePrice()` method, but with the following statement:

    ```java
    return super.getRegularPrice() * 0.5;
    ```

    You may continue with the given code for `Book.java` as follows:

    ```java linenums="1" hl_lines="13" title="Book.java"
    public class Book extends Product {
    	private String publisher;
    	private int yearPublished;

    	// Creates a new instance of Book
    	public Book(double regularPrice, String publisher,
    							int yearPublished) {
    		super(regularPrice);
    		setPublisher(publisher);
    		setYearPublished(yearPublished);
    	}

    	// Implement abstract method here

    	public String getPublisher() { return publisher; }

    	public void setPublisher(String publisher) {
    		this.publisher = publisher;
    	}

    	public int getYearPublished() { return yearPublished; }

    	public void setYearPublished(int yearPublished) {
    		this.yearPublished = yearPublished;
    	}
    }
    ```

4.  Run `Main.java`.

    ```java linenums="1" hl_lines="6-9" title="Main.java"
    public class Main {
    	public static void main(String[] args) {
    		// Declare and create Product array of size 5
    		Product[] pa = new Product[5];

    		/**
    		  * Create object instances and assign them to
    		  * the type of Product.
    		  */
    		pa[0] = new TV(1000, "Samsung", 30);
    		pa[1] = new TV(2000, "Sony", 50);
    		pa[2] = new MP3Player(250, "Apple", "blue");
    		pa[3] = new Book(34, "Sun Press", 1992);
    		pa[4] = new Book(15, "Korea Press", 1986);

    		// Compute total regular price and total sale price
    		double totalRegularPrice = 0;
    		double totalSalePrice = 0;

    		for(int i = 0; i < pa.length; i++) {
    			/**
    			  * Call a method of the superclass to get
    			  * the regular price.
    			  */
    			totalRegularPrice += pa[i].getRegularPrice();

    			/**
    			  * Since the sale price is computed differently
    			  * depending on the product type, overriding
    			  * (implementation) method of the object instance
    			  * of the subclass gets invoked. This is runtime
    			  * polymorphic behavior.
    			  */
    			totalSalePrice += pa[i].computeSalePrice();

    			System.out.println("Item number " + i
    				+ ": Type = " + pa[i].getClass().getName()
    				+ ", Regular price = " + pa[i].getRegularPrice()
    				+ ", Sale price = " + pa[i].computeSalePrice());
    		}
    		System.out.println("totalRegularPrice = "
    			+ totalRegularPrice);
    		System.out.println("totalSalePrice = " + totalSalePrice);
    	}
    }
    ```

    You should observe the following output results:

        Item number 0: Type = myonlineshop.TV, Regular price = 1000.0, Sale price = 800.0
        Item number 1: Type = myonlineshop.TV, Regular price = 2000.0, Sale price = 1600.0
        Item number 2: Type = myonlineshop.MP3Player, Regular price = 250.0, Sale price = 225.0
        Item number 3: Type = myonlineshop.Book, Regular price = 34.0, Sale price = 17.0
        Item number 4: Type = myonlineshop.Book, Regular price = 15.0, Sale price = 7.5
        totalRegularPrice = 3299.0
        totalSalePrice = 2649.5
