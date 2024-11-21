<h2>Inheritence (Generalization)</h2>
<p>It is a type of realationship, where one class inherits/aquires/extends the properities and methods of another class.</p>
<p>It represents <strong>"Is a"</strong> relationship</p>
<p>Since, child class will have all the properties and methods of parent class, child is a version of parent with some optional additional functionality.</p>
<p>So, we can also say, child "is a" type of parent</p>
<h3>Example-1 :</h3>

```java
// Parent class
class Animal {


	h2
    void eat() {
        System.out.println("This animal eats food.");
    }

    void sleep() {
        System.out.println("This animal sleeps.");
    }
}

// Child class inheriting from Animal
class Dog extends Animal {
    void bark() {
        System.out.println("The dog barks.");
    }
}

// Child class inheriting from Animal
class Cat extends Animal {
    void meow() {
        System.out.println("The cat meows.");
    }
}

// Main class
public class InheritanceExample {
    public static void main(String[] args) {
        // Create a Dog object
        Dog dog = new Dog();
        dog.eat();   // Inherited from Animal
        dog.sleep(); // Inherited from Animal
        dog.bark();  // Unique to Dog

        // Create a Cat object
        Cat cat = new Cat();
        cat.eat();   // Inherited from Animal
        cat.sleep(); // Inherited from Animal
        cat.meow();  // Unique to Cat
    }
}

```

<p>Here, Dog and Cat inherits from animal, simply we can say,</p>
<ul>
	<li>Dog <strong>Is a</strong> Animal</li>
	<li>Cat <strong>Is a</strong> Animal</li>
</ul>

<h3>Example-2 :</h3>

```java
// Parent class
class User {
    String username;

    void login() {
        System.out.println(username + " has logged in.");
    }

    void logout() {
        System.out.println(username + " has logged out.");
    }
}

// Admin class inheriting User
class Admin extends User {
    void manageUsers() {
        System.out.println(username + " is managing users.");
    }
}

// Customer class inheriting User
class Customer extends User {
    void browseProducts() {
        System.out.println(username + " is browsing products.");
    }
}

// Vendor class inheriting User
class Vendor extends User {
    void manageInventory() {
        System.out.println(username + " is managing inventory.");
    }
}

// Main class
public class RealtimeInheritanceExample {
    public static void main(String[] args) {
        // Admin user
        Admin admin = new Admin();
        admin.username = "AdminUser";
        admin.login();
        admin.manageUsers();
        admin.logout();

        // Customer user
        Customer customer = new Customer();
        customer.username = "CustomerUser";
        customer.login();
        customer.browseProducts();
        customer.logout();

        // Vendor user
        Vendor vendor = new Vendor();
        vendor.username = "VendorUser";
        vendor.login();
        vendor.manageInventory();
        vendor.logout();
    }
}
```

<p>In the above example, we can see Admin,Customer,Vendor Inherits from User</p>
<p>Simply we can say like</p>
<ul>
	<li>Admin <strong>Is a</strong> User</li>
	<li>Customer <strong>Is a</strong> User</li>
	<li>Vendor <strong>Is a</strong> User</li>
</ul>
<p>It is also called as <strong>generalization</strong></p>
<h3>Why it is called as generalization?</h3>
<p>It’s called generalization because it takes what is common among different things and puts it together in one general category (Parent).</p>
<ul>
	<li>You see a Dog and a Cat. Both are animals, and both can eat and sleep. So, instead of saying "Dogs eat and sleep" and "Cats eat and sleep" separately, you create a general category called Animal and say, "All animals can eat and sleep."</li>
	<li>Then, you can still say, "Dogs can bark" and "Cats can meow," which are their special features.</li>
</ul>
<p>Generalization means finding common things (like eating and sleeping) and putting them in a parent group (like Animal), while still allowing for differences in the child groups (like Dog or Cat).</p>


<h2>Interface (Realization)</h2>
<p>It is a type of realtionship, where one class implements an interface</p>
<p>Simply, a class or object promises to follow the rules or instructions defined by an interface.</p>
<p>It is also called as <strong>'Realization'</strong></p>

<h3>Example-1 :</h3>

```java
// The Interface (contract)
interface Payment {
    void initiatePayment(double amount);
    void processPayment();
    void confirmPayment();
}

// Class that realizes the interface: Credit Card Payment
class CreditCardPayment implements Payment {
    public void initiatePayment(double amount) {
        System.out.println("Credit Card Payment of $" + amount + " initiated.");
    }

    public void processPayment() {
        System.out.println("Processing Credit Card Payment...");
    }

    public void confirmPayment() {
        System.out.println("Credit Card Payment confirmed.");
    }
}

// Class that realizes the interface: PayPal Payment
class PayPalPayment implements Payment {
    public void initiatePayment(double amount) {
        System.out.println("PayPal Payment of $" + amount + " initiated.");
    }

    public void processPayment() {
        System.out.println("Processing PayPal Payment...");
    }

    public void confirmPayment() {
        System.out.println("PayPal Payment confirmed.");
    }
}

// Main Class
public class PaymentSystemExample {
    public static void main(String[] args) {
        // Using Credit Card Payment
        Payment creditCard = new CreditCardPayment();
        creditCard.initiatePayment(100.00);
        creditCard.processPayment();
        creditCard.confirmPayment();

        // Using PayPal Payment
        Payment paypal = new PayPalPayment();
        paypal.initiatePayment(50.00);
        paypal.processPayment();
        paypal.confirmPayment();
    }
}
```

<p>In the above example , we can observer, CreditCardPayment and PayPalPayment implements Payment interface</p>
<p>Each payment method (CreditCardPayment, PayPalPayment) follows the same structure but implements the behavior differently.</p>

<h2>Composition</h2>
<p>It is a type of relationship, where one object is a <strong>part of</strong> another object.</p>
<p>It represents <strong>"Part Of"</strong> relationship</p>
<p>It is a type of <strong>"Part-Whole"</strong> relationship, where if whole gets destroyed, the parts will also get destroyed</p>

<p>Here are some examples of <strong>Whole-Part</strong> relationships:</p>
<ol>
    <li>
        <p><strong>Car and Engine/Wheels/Doors</strong></p>
        <ul>
            <li><strong>Whole:</strong> Car</li>
            <li><strong>Parts:</strong> Engine, wheels, doors</li>
        </ul>
    </li>
    <li>
        <p><strong>House and Rooms/Windows/Doors</strong></p>
        <ul>
            <li><strong>Whole:</strong> House</li>
            <li><strong>Parts:</strong> Rooms, windows, doors</li>
        </ul>
    </li>
    <li>
        <p><strong>Computer and CPU/Hard Drive/Monitor/Keyboard</strong></p>
        <ul>
            <li><strong>Whole:</strong> Computer</li>
            <li><strong>Parts:</strong> CPU, hard drive, monitor, keyboard</li>
        </ul>
    </li>
    <li>
        <p><strong>Book and Chapters/Pages/Paragraphs</strong></p>
        <ul>
            <li><strong>Whole:</strong> Book</li>
            <li><strong>Parts:</strong> Chapters, pages, paragraphs</li>
        </ul>
    </li>
    <li>
        <p><strong>Body and Heart/Brain/Lungs/Arms/Legs</strong></p>
        <ul>
            <li><strong>Whole:</strong> Body</li>
            <li><strong>Parts:</strong> Heart, brain, lungs, arms, legs</li>
        </ul>
    </li>
    <li>
        <p><strong>Tree and Branches/Leaves/Roots</strong></p>
        <ul>
            <li><strong>Whole:</strong> Tree</li>
            <li><strong>Parts:</strong> Branches, leaves, roots</li>
        </ul>
    </li>
    <li>
        <p><strong>Library and Books/Shelves/Tables</strong></p>
        <ul>
            <li><strong>Whole:</strong> Library</li>
            <li><strong>Parts:</strong> Books, shelves, tables</li>
        </ul>
    </li>
    <li>
        <p><strong>Phone and Battery/Screen/Camera</strong></p>
        <ul>
            <li><strong>Whole:</strong> Phone</li>
            <li><strong>Parts:</strong> Battery, screen, camera</li>
        </ul>
    </li>
    <li>
        <p><strong>Airplane and Wings/Engine/Tail</strong></p>
        <ul>
            <li><strong>Whole:</strong> Airplane</li>
            <li><strong>Parts:</strong> Wings, engine, tail</li>
        </ul>
    </li>
    <li>
        <p><strong>Human Face and Eyes/Nose/Mouth/Ears</strong></p>
        <ul>
            <li><strong>Whole:</strong> Face</li>
            <li><strong>Parts:</strong> Eyes, nose, mouth, ears</li>
        </ul>
    </li>
</ol>




<h3>Example-1 :</h3>

```java
// The Transaction class - a part of the BankAccount
class Transaction {
    private Date date;
    private String type; // e.g., "Deposit" or "Withdrawal"
    private double amount;
}

// The BankAccount class - composed of multiple Transaction objects
class BankAccount {
    private String accountNumber;
    private double balance;
    private List<Transaction> transactions;
}

```

<p>In the above examples, we can observe that, Transactions are <strong>Part Of</strong> Bank Account</p>
<p>If we delete bankaccount, transations will also get deleted</p>
<p>So, we can say, Transactions are <strong>Part Of</strong> BackAccount</p>


<h3>Aggregation</h3>
<p>It is a type of relationship, where one object has a reference to another object</p>
<p>It represents <strong>Has a</strong> relationship</p>
<p>It is also a type of <strong>Part-Whole</strong> relationship, where The part (object) can exist independently of the whole object. If the whole object is destroyed, the part can still exist.</p>
<p>Aggregation is a weaker form of ownership than composition. The lifetime of the part object is not controlled by the whole.</p>
<p>Here’s a list of <strong>Whole-Part</strong> examples for <strong>aggregation</strong> where the part can exist independently of the whole:</p>

<ol>
    <li>
        <p><strong>Library and Books</strong></p>
        <ul>
            <li><strong>Whole:</strong> Library</li>
            <li><strong>Part:</strong> Books</li>
            <li>A book can exist independently of the library and can be part of other libraries or collections.</li>
        </ul>
    </li>
    <li>
        <p><strong>Department and Employees</strong></p>
        <ul>
            <li><strong>Whole:</strong> Department</li>
            <li><strong>Part:</strong> Employees</li>
            <li>Employees can work in other departments or organizations, and their existence is independent of the department they work in.</li>
        </ul>
    </li>
    <li>
        <p><strong>University and Students</strong></p>
        <ul>
            <li><strong>Whole:</strong> University</li>
            <li><strong>Part:</strong> Students</li>
            <li>Students are not dependent on the university for their existence and can transfer between universities.</li>
        </ul>
    </li>
    <li>
        <p><strong>Team and Players</strong></p>
        <ul>
            <li><strong>Whole:</strong> Team</li>
            <li><strong>Part:</strong> Players</li>
            <li>Players can switch teams or exist independently, e.g., when they are free agents.</li>
        </ul>
    </li>
    <li>
        <p><strong>Company and Employees</strong></p>
        <ul>
            <li><strong>Whole:</strong> Company</li>
            <li><strong>Part:</strong> Employees</li>
            <li>Employees can leave the company and still exist independently, perhaps joining another company.</li>
        </ul>
    </li>
    <li>
        <p><strong>Team and Coaches</strong></p>
        <ul>
            <li><strong>Whole:</strong> Team</li>
            <li><strong>Part:</strong> Coaches</li>
            <li>Coaches can work for other teams, and their existence doesn’t depend on a single team.</li>
        </ul>
    </li>
    <li>
        <p><strong>Car and Tires</strong></p>
        <ul>
            <li><strong>Whole:</strong> Car</li>
            <li><strong>Part:</strong> Tires</li>
            <li>Tires can exist without the car and can be used on other cars, so the car doesn’t control the tire's lifecycle.</li>
        </ul>
    </li>
    <li>
        <p><strong>Course and Students</strong></p>
        <ul>
            <li><strong>Whole:</strong> Course</li>
            <li><strong>Part:</strong> Students</li>
            <li>A student can take multiple courses, and their existence doesn’t depend on any single course.</li>
        </ul>
    </li>
    <li>
        <p><strong>Project and Team Members</strong></p>
        <ul>
            <li><strong>Whole:</strong> Project</li>
            <li><strong>Part:</strong> Team Members</li>
            <li>Team members can work on different projects at different times and are not inherently tied to a specific project.</li>
        </ul>
    </li>
    <li>
        <p><strong>Author and Books</strong></p>
        <ul>
            <li><strong>Whole:</strong> Author</li>
            <li><strong>Part:</strong> Books</li>
            <li>An author can write multiple books, and the books exist even if the author no longer writes.</li>
        </ul>
    </li>
</ol>


```java
// The Book class - a part of the Library
class Book {
    private String title;
    private String author;

    public Book(String title, String author) {
        this.title = title;
        this.author = author;
    }
}

// The Library class - aggregates multiple Book objects
import java.util.List;

class Library {
    private String name;
    private List<Book> books;

    public Library(String name) {
        this.name = name;
        this.books = new ArrayList<>();
    }

    public void addBook(Book book) {
        books.add(book);
    }
}

// Instantiating the objects
public class Main {
    public static void main(String[] args) {
        // Creating Book objects (part of the aggregation)
        Book book1 = new Book("1984", "George Orwell");
        Book book2 = new Book("To Kill a Mockingbird", "Harper Lee");

        // Creating a Library object (whole)
        Library library = new Library("Central Library");

        // Adding books to the library
        library.addBook(book1);
        library.addBook(book2);
    }
}
```
<ul>
	<li>Book Class: Represents a book, independent of the Library.</li>
	<li>Library Class: Aggregates multiple Book objects. The Library does not own the Book objects, meaning the Book objects can exist independently of the Library.</li>
	<li>The instantiation demonstrates the aggregation relationship, where the Library holds references to Book objects but does not manage their lifecycle.</li>
</ul>

<h3>Association</h3>
<p>It is a type of relationship, where one object has a reference to another object. but there is no Part-Whole Relationship</p>
<p>It can be Bidirectional or Unidirectional</p>
<p>It doesn't represent any ownership / lifetime dependency like composition or aggregatiom</p>
<p>It represents <strong>"Has a"</strong> relationship</p>
<p>Association can have different types of multiplicity:</p>
<ul>
	<li>One-to-One: One object is associated with exactly one other object.</li>
	<li>One-to-Many: One object is associated with multiple objects.</li>
	<li>Many-to-Many: Multiple objects are associated with multiple objects.</li>
</ul>

<p><strong>Examples : </strong></p>
<p>There should not be any Part-Whole relationship, but one object should use another object</p>
<ol>
    <li>
        <strong>Teacher and Student</strong>
        <ul>
            <li><strong>Relationship:</strong> One-to-Many or Many-to-Many</li>
            <li><strong>Explanation:</strong> A Teacher can be associated with many Students, and a Student can have multiple Teachers. Both Teacher and Student objects can exist independently of each other.</li>
        </ul>
    </li>
    <li>
        <strong>Customer and Orders</strong>
        <ul>
            <li><strong>Relationship:</strong> One-to-Many or Many-to-Many</li>
            <li><strong>Explanation:</strong> A Customer can place multiple Orders, and Orders can be associated with multiple Customers (in case of shared orders). The Customer and Order objects are independent of each other.</li>
        </ul>
    </li>
    <li>
        <strong>Car and Driver</strong>
        <ul>
            <li><strong>Relationship:</strong> Many-to-Many</li>
            <li><strong>Explanation:</strong> A Car is driven by a Driver. A Driver may drive many Cars, and a Car can have multiple Drivers over time. Both objects interact but are independent of each other's lifecycle.</li>
        </ul>
    </li>
    <li>
        <strong>Doctor and Patient</strong>
        <ul>
            <li><strong>Relationship:</strong> Many-to-Many</li>
            <li><strong>Explanation:</strong> A Doctor can treat many Patients, and a Patient can have multiple Doctors. The Doctor and Patient objects exist independently of each other.</li>
        </ul>
    </li>
    <li>
        <strong>Author and Book</strong>
        <ul>
            <li><strong>Relationship:</strong> Many-to-Many</li>
            <li><strong>Explanation:</strong> An Author can write many Books, and a Book can have multiple Authors. The Author and Book objects exist independently, and one does not control the lifecycle of the other.</li>
        </ul>
    </li>
        <strong>Product and Category</strong>
        <ul>
            <li><strong>Relationship:</strong> One-to-Many</li>
            <li><strong>Explanation:</strong> A Product belongs to a Category, but a Category can contain multiple Products. Products can be moved between categories, and categories can exist without specific Products.</li>
        </ul>
    </li>
    <li>
        <strong>Teacher and Subject</strong>
        <ul>
            <li><strong>Relationship:</strong> Many-to-Many</li>
            <li><strong>Explanation:</strong> A Teacher teaches one or more Subjects, and each Subject can have multiple Teachers. Both Teacher and Subject objects can exist independently.</li>
        </ul>
    </li>
</ol>


<h3>Example :</h3>

```java
import java.util.ArrayList;
import java.util.List;

class Doctor {
    String name;
    List<Patient> patients = new ArrayList<>();

    Doctor(String name) {
        this.name = name;
    }

    void addPatient(Patient patient) {
        patients.add(patient);
    }
}

import java.util.ArrayList;
import java.util.List;

class Patient {
    String name;
    List<Doctor> doctors = new ArrayList<>();

    Patient(String name) {
        this.name = name;
    }

    void addDoctor(Doctor doctor) {
        doctors.add(doctor);
    }
}


public class HealthcareSystem {
    public static void main(String[] args) {
        // Create Doctors
        Doctor doctor1 = new Doctor("Dr. Alice");
        Doctor doctor2 = new Doctor("Dr. Bob");

        // Create Patients
        Patient patient1 = new Patient("John Doe");
        Patient patient2 = new Patient("Jane Smith");

        // Associate Doctors with Patients
        doctor1.addPatient(patient1);
        doctor1.addPatient(patient2);
        doctor2.addPatient(patient1);

        // Associate Patients with Doctors
        patient1.addDoctor(doctor1);
        patient1.addDoctor(doctor2);
        patient2.addDoctor(doctor1);

        // Display the associations
        System.out.println(doctor1.name + " is treating:");
        for (Patient patient : doctor1.patients) {
            System.out.println(patient.name);
        }

        System.out.println(doctor2.name + " is treating:");
        for (Patient patient : doctor2.patients) {
            System.out.println(patient.name);
        }

        System.out.println(patient1.name + " is being treated by:");
        for (Doctor doctor : patient1.doctors) {
            System.out.println(doctor.name);
        }

        System.out.println(patient2.name + " is being treated by:");
        for (Doctor doctor : patient2.doctors) {
            System.out.println(doctor.name);
        }
    }
}
```

<p>In the above example, doctor has pations reference and patient has doctors reference, none of the class represents Part-Whole Relationship.</p>
<p>It is represnting bidirectional relationships</p>
<p>It is many-to-many relationship</p>

<h3>Dependency</h3>
<p>It is a type of relationship, where one object depends on another object to perform specific operation.</p>
<p>It represents <strong>"Uses"</strong> relationship</p>
<p>It doesn't represent Part-Whole relationship and it shows heavy dependency on another object</p>

<p><strong>Example :</strong></p>

```java
class Printer {
    public void print(String message) {
        System.out.println("Printing: " + message);
    }
}

class Library {
    private Printer printer;

    // Constructor Dependency Injection
    public Library(Printer printer) {
        this.printer = printer;
    }

    public void printBookList(String bookList) {
        printer.print(bookList);  // Library depends on Printer to print
    }
}

public class Main {
    public static void main(String[] args) {
        Printer printer = new Printer(); // Create Printer object
        Library library = new Library(printer); // Library depends on Printer

        library.printBookList("Book1, Book2, Book3"); // Uses Printer to print
    }
}
```

<p>In the above example, library uses printer to perform printBookList operation and without printer we can't perform that operation</p>


<h2>Comparision</h2>
<table border="1">
    <tr>
        <th><strong>Aspect</strong></th>
        <th><strong>Composition</strong></th>
        <th><strong>Aggregation</strong></th>
        <th><strong>Association</strong></th>
        <th><strong>Dependency</strong></th>
    </tr>
    <tr>
        <td><strong>Definition</strong></td>
        <td>Strong "Whole-Part" relationship where the part is dependent on the whole.</td>
        <td>"Whole-Part" relationship where the part can exist independently of the whole.</td>
        <td>General relationship where objects interact but do not depend on each other for their existence.</td>
        <td>A weaker relationship where one object depends on another for functionality.</td>
    </tr>
    <tr>
        <td><strong>Lifetime</strong></td>
        <td>The part’s lifetime is tied to the whole object’s lifetime.</td>
        <td>The part can exist independently even if the whole object is destroyed.</td>
        <td>Objects have independent lifetimes.</td>
        <td>The dependent object can exist independently, but depends on another object for specific functionality.</td>
    </tr>
    <tr>
        <td><strong>Ownership</strong></td>
        <td>The whole object owns the part, and part cannot exist without the whole.</td>
        <td>The whole object doesn’t own the part, and part can be shared by multiple objects.</td>
        <td>No ownership, objects are related but do not control each other.</td>
        <td>One object uses or relies on another object’s functionality temporarily.</td>
    </tr>
    <tr>
        <td><strong>Example</strong></td>
        <td>Car has an Engine. If Car is destroyed, Engine is destroyed.</td>
        <td>A School has Teachers. Teachers can exist even if the School is destroyed.</td>
        <td>A Student uses a Library. Both can exist independently.</td>
        <td>A Student depends on a Teacher for learning.</td>
    </tr>
    <tr>
        <td><strong>Strength of Relationship</strong></td>
        <td>Strong relationship (tight coupling).</td>
        <td>Weak relationship (loose coupling).</td>
        <td>Loose relationship, can be one-to-one, one-to-many, or many-to-many.</td>
        <td>Weakest relationship, often one object calls methods of another.</td>
    </tr>
    <tr>
        <td><strong>Diagram Notation</strong></td>
        <td>Diamond at the whole side.</td>
        <td>Empty diamond at the whole side.</td>
        <td>Line between objects (typically with multiplicity).</td>
        <td>Dashed line with an arrow pointing from the dependent object to the dependency.</td>
    </tr>
</table>