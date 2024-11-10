<h1>Design Petterns</h1>
<p>Design patterns are standard solutions to commonly occurring problems in software design.</p>
<p>They’re like templates or blueprints that can be applied to solve specific issues when designing software systems</p>
<p>Rather than solving problems from scratch, developers can use these patterns to achieve a flexible, reusable, and maintainable code structure.</p>
<p><strong>Key Points</strong></p>
<ul>
	<li>A design pattern is like a general idea for solving a problem in programming. It's not just a piece of code you can copy; it's a concept that you can adapt to fit your specific situation.</li>
	<li>People often mix up patterns with algorithms. An algorithm is a specific set of steps to achieve a goal, like a cooking recipe. In contrast, a pattern is more like a blueprint for building something. It shows you what the end result should look like but leaves the details of how to get there up to you.</li>
</ul>
<p>So, while an algorithm tells you exactly what to do, a pattern gives you a guide that you can modify for your own needs.</p>
<p>Design patterns can be classified into three main categories based on their purpose and use. Here’s a simple breakdown:</p>
<ul>
	<li><strong>Creational Patterns</strong> :  Deals with how objects are created.</li>
	<li><strong>Structural Patterns</strong> :  Deals with assembling objects and classes into larger structures.</li>
	<li><strong>Behavioral Patterns</strong> :  Deals with how objects interact and communicate with each other.</li>
</ul>

<h2>Structural Patterns</h2>
<p>Structural patterns are like blueprints how different classes and objects can be combined/organized together to form efficent/bigger structures for making system more maintainble,flexible and reusable</p>
<p>Types of structural patterns</p>
<ol>
	<li>Adapter Pattern</li>
	<li>Bridge Pattern</li>
	<li>Decorator Pattern</li>
	<li>Fascade Pattern</li>
	<li>Composite Pattern</li>
	<li>FlyWeight Pattern</li>
	<li>Proxy Pattern</li>
</ol>
<h3>Adpater Pattern</h3>
<p>It is a structural design pattern which allows different incompatable interaces work together by creating a adpater class that converts the interface of one class into another inteface that is expected by the client.</p>
<p><strong>Use Cases :</strong></p>
<ul>
	<li>When you have incompatible interfaces but need them to work together.</li>
	<li>When you want to use a class that lacks the interface you need.</li>
	<li>When working with legacy systems where the code can’t be modified, but you need to integrate it with a new system.</li>
</ul>
<p><strong>Components :</strong></p>
<ul>
	<li><strong>Target Interface :</strong>Defines the interface expected by the client. It represents the set of operations that the client code can use. It’s the common interface that the client code interacts with.</li>
	<li><strong>Adaptee :</strong>The existing class or system with an incompatible interface that needs to be integrated into the new system. It’s the class or system that the client code cannot directly use due to interface mismatches.</li>
	<li><strong>Adapter :</strong>A class that implements the target interface and internally uses an instance of the adaptee to make it compatible with the target interface. It acts as a bridge, adapting the interface of the adaptee to match the target interface.</li>
	<li><strong>Client :</strong>The code that uses the target interface to perform operations.</li>
</ul>
<img src="https://www.codurance.com/hubfs/Imported_Blog_Media/adapter-pattern-uml.png">
<p><strong>Example :</strong></p>

```java
// Target Interface: The interface that the client expects to use
interface Printer {
    public void print();  // This method is expected by the client
}

// Adaptee: The existing class with an incompatible interface
class OldPrinter {
    // This is the old method that doesn't fit the target interface
    public void print_text() {
        System.out.println("printing using old printer(different interface)");
    }
}

// NewPrinter: This class implements the Target Interface
class NewPrinter implements Printer {
    
    @Override
    public void print() {
        // This is the new method that works with the target interface
        System.out.println("printing using new printer(target interface)");
    }
}

// Adapter: This class makes the OldPrinter compatible with the Printer interface
class OldPrinterAdapter implements Printer {
    
    @Override
    public void print() {
        // Inside the adapter, we create an instance of OldPrinter
        OldPrinter printer = new OldPrinter();
        
        // The adapter calls the incompatible method print_text() of OldPrinter
        printer.print_text();
    }
}

// Client: This class uses the Printer interface, expecting any compatible printer
class Client {
    public void printData(Printer printer) {
        // The client simply calls the print method on any object that implements Printer
        printer.print();
    }
}

public class Main {
    public static void main(String[] args) {
        // Create an instance of the client
        Client client = new Client();
        
        // Create instances of both NewPrinter and OldPrinter (with Adapter)
        NewPrinter newPrint = new NewPrinter();
        OldPrinter oldPrint = new OldPrinter();
        
        // Client can print using the new printer, as it implements the Printer interface
        client.printData(newPrint); // Output: printing using new printer(target interface)
        
        // Trying to pass OldPrinter directly will cause an error since it doesn't implement Printer
        // client.printData(oldPrint); // Uncommenting this line will raise a compile-time error

        // To use the old printer, we need to use the adapter that wraps the OldPrinter
        OldPrinterAdapter oldAdapter = new OldPrinterAdapter();
        
        // Now, the client can print using the adapter, which adapts the old printer
        client.printData(oldAdapter); // Output: printing using old printer(different interface)
    }
}
```
<ul>
	<li><strong>Target Interface :</strong>Printer</li>
	<li><strong>Adaptee :</strong>OldPrinter</li>
	<li><strong>Target Implementation :</strong>NewPrinter</li>
	<li><strong>Adapater :</strong>OldPrinterAdapater</li>
	<li><strong>Client :</strong>Client</li>
</ul>
<p>The Adapter Pattern enables a class (OldPrinter) with an incompatible interface to work with a client expecting a different interface (Printer) by providing an adapter (OldPrinterAdapter) that translates the method calls.</p>

<p><strong>Real Time Examples :</strong></p>
<ul>
	<li><strong>Payment Gateways: </strong></li>
	<ul>
		<li><strong>Example :</strong>A shopping website integrating different payment gateways (PayPal, Stripe, Square), but each has a different API.</li>
		<li><strong>Adapter :</strong>An adapter class can adapt multiple payment methods to be compatible a common interface the website is using.</li>
	</ul>
	<li><strong>Database Connectors: </strong></li>
	<ul>
		<li>A web application that needs to connect to multiple types of databases (like MySQL, PostgreSQL, and MongoDB) but the application only supports one type of database connection interface.</li>
		<li>An ORM (Object-Relational Mapping) library, such as Hibernate, serves as an adapter between the application and the various databases.</li>
	</ul>
</ul>
