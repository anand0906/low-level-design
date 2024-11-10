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


<h3>Bridge Design Pattern</h3>
<p>It is a structural design pattern which separates the functionality (abstraction) from its implementation when there is multiple variations of functionality in its implementations, so that both functionality and implementations can be modified without changing existance logic.</p>
<br>
<p>Suppose, there is a interface with two functionalities(abstract methods), if there are multiple variations for each functionality. instead of creating multiple implementations for each combinations of functionlities, we can separate interface into two functionlity based interfaces.So, that we can use respective implementation of functionality in objects. we can easily modify the both functionalitis without effecting existance objects</p>
<br>
<p>Simply, it is structural design pattern which separates abstractions from its implementations, so that both can change independently without any effect.</p>
<p><strong>Use Cases</strong></p>
<ul>
	<li>You have a growing number of classes due to a mix of multiple types of abstractions and implementations, and you want to reduce the complexity.</li>
	<li>You want to keep the abstraction and implementation loosely coupled.</li>
	<li>You need to be able to change either the abstraction or the implementation independently.</li>
	<li>Use if you need to be able to switch implementations at runtime.</li>
</ul>
<p><strong>Components :</strong></p>
<ul>
	<li><strong>Abstraction: </strong>Given abstraction with multiple functionalities</li>
	<li><strong>Implementor: </strong>Interface after separating functionalities from abtraction</li>
	<li><strong>Concrete Implementors: </strong>Implementation of implementors</li>
	<li><strong>Refined Abtraction: </strong>Modfied Abstraction after applying bridge pattern</li>
</ul>

<p><strong>Example: </strong></p>
<p><strong>Case 1: Without the Bridge Pattern (Tightly Coupled)</strong></p>
<p>In this case, the <strong>Shape</strong> and <strong>Color</strong> are tightly coupled, meaning that the <strong>Shape</strong> class directly depends on the color functionality. If you want to add a new color or shape, you’ll need to modify the existing classes.</p>

<p><strong>Code:</strong></p>

```java
interface Shape {
    void getShape();
    void getColor();
}

class RedCircle implements Shape {
    public void getShape() {
        System.out.println("Shape of Object is Circle");
    }
    
    public void getColor() {
        System.out.println("Color of Circle is Red");
    }
}

class BlueCircle implements Shape {
    public void getShape() {
        System.out.println("Shape of Object is Circle");
    }
    
    public void getColor() {
        System.out.println("Color of Circle is Blue");
    }
}

class RedRectangle implements Shape {
    public void getShape() {
        System.out.println("Shape of Object is Rectangle");
    }
    
    public void getColor() {
        System.out.println("Color of Rectangle is Red");
    }
}

class BlueRectangle implements Shape {
    public void getShape() {
        System.out.println("Shape of Object is Rectangle");
    }
    
    public void getColor() {
        System.out.println("Color of Rectangle is Blue");
    }
}

public class Main {
    public static void main(String[] args) {
        Shape redCircle = new RedCircle();
        redCircle.getShape();
        redCircle.getColor();

        Shape blueRectangle = new BlueRectangle();
        blueRectangle.getShape();
        blueRectangle.getColor();
    }
}
```

<p><strong>Explanation of Case 1 (Without Bridge Pattern):</strong></p>
<ul>
    <li>In this approach, every <strong>combination of shape and color</strong> requires a separate class. For example, <strong>RedCircle</strong> and <strong>BlueCircle</strong> are separate classes for each color and shape combination.</li>
    <li><strong>Drawback</strong>: 
        <ul>
            <li>If you need to add another color (e.g., <strong>Green</strong>), you'll need to create new classes for every shape (e.g., <strong>GreenCircle</strong>, <strong>GreenRectangle</strong>).</li>
            <li>If you want to add another shape (e.g., <strong>Triangle</strong>), you would need to create multiple classes for each color (e.g., <strong>RedTriangle</strong>, <strong>BlueTriangle</strong>), leading to code duplication and making the system harder to maintain.</li>
        </ul>
    </li>
</ul>

<p><strong>Case 2: With the Bridge Pattern (Loosely Coupled)</strong></p>
<p>Now, let’s use the <strong>Bridge Pattern</strong> to decouple the <strong>Shape</strong> (abstraction) from the <strong>Color</strong> (implementation). With this pattern, the <strong>Shape</strong> and <strong>Color</strong> can vary independently.</p>

<p><strong>Code:</strong></p>

```java
interface Shape {
    void getShape();
    void getColor();
}

interface Color {
    String getColor();
}

class Red implements Color {
    public String getColor() {
        return "Red";
    }
}

class Blue implements Color {
    public String getColor() {
        return "Blue";
    }
}

class Circle implements Shape {
    private Color color;

    Circle(Color color) {
        this.color = color;
    }

    public void getShape() {
        System.out.println("Shape of Object is Circle");
    }

    public void getColor() {
        System.out.println("Color of Circle is " + this.color.getColor());
    }
}

class Rectangle implements Shape {
    private Color color;

    Rectangle(Color color) {
        this.color = color;
    }

    public void getShape() {
        System.out.println("Shape of Object is Rectangle");
    }

    public void getColor() {
        System.out.println("Color of Rectangle is " + this.color.getColor());
    }
}

public class Main {
    public static void main(String[] args) {
        Color red = new Red();
        Color blue = new Blue();

        Shape redCircle = new Circle(red);
        redCircle.getShape();
        redCircle.getColor();

        Shape blueRectangle = new Rectangle(blue);
        blueRectangle.getShape();
        blueRectangle.getColor();

        // You can now change colors or shapes without creating a new class for each combination
        Shape blueCircle = new Circle(blue);
        blueCircle.getShape();
        blueCircle.getColor();
    }
}
```

<p><strong>Explanation of Case 2 (With Bridge Pattern):</strong></p>
<ul>
    <li>In this case, we have <strong>two separate interfaces</strong>: 
        <ul>
            <li><strong>Shape</strong> (Abstraction) handles high-level shape functionality (like <code>getShape()</code> and <code>getColor()</code>).</li>
            <li><strong>Color</strong> (Implementer) handles color-specific functionality (like <code>getColor()</code>).</li>
        </ul>
    </li>
    <li><strong>Concrete Implementers</strong>: <strong>Red</strong> and <strong>Blue</strong> provide the actual implementation for the <code>getColor()</code> method.</li>
    <li><strong>Refined Abstractions</strong>: <strong>Circle</strong> and <strong>Rectangle</strong> implement the <strong>Shape</strong> interface. They each hold a reference to a <strong>Color</strong> object and delegate the color functionality to the color object.</li>
    <li>This setup means:
        <ul>
            <li>You can easily change the <strong>color</strong> or the <strong>shape</strong> without needing to create new classes for every combination.</li>
            <li>To add a new <strong>color</strong>, you only need to create a new <strong>Color</strong> class (like <strong>Green</strong>).</li>
            <li>To add a new <strong>shape</strong>, you can simply add a new <strong>Shape</strong> class (like <strong>Triangle</strong>).</li>
        </ul>
    </li>
    <li><strong>Benefit:</strong> This greatly reduces duplication and makes the system more flexible and maintainable.</li>
</ul>
<p><strong>Example Output:</strong></p>

```java
Shape of Object is Circle
Color of Circle is Red
Shape of Object is Rectangle
Color of Rectangle is Blue
Shape of Object is Circle
Color of Circle is Blue
```

<p><strong>Summary of Differences:</strong></p>
<ul>
    <li><strong>Without the Bridge Pattern:</strong>
        <ul>
            <li>You need a new class for every combination of shape and color.</li>
            <li>Leads to code duplication.</li>
            <li>Harder to maintain and extend as the number of variations increases.</li>
        </ul>
    </li>
    <li><strong>With the Bridge Pattern:</strong>
        <ul>
            <li><strong>Shape</strong> and <strong>Color</strong> are separated into different hierarchies.</li>
            <li>You can easily add new shapes or colors without modifying existing code.</li>
            <li>The system is more maintainable, flexible, and scalable.</li>
        </ul>
    </li>
</ul>

<p>This makes the <strong>Bridge Pattern</strong> ideal when you have multiple variations of both abstractions and implementations, as it allows for easy extension without causing modification to existing code.</p>


<p><strong>Example-2</strong></p>
<p><strong>Case 1: Without Bridge Pattern (Tightly Coupled)</strong></p>
<p>In this case, the <code>DocumentViewer</code> class directly depends on specific document types (e.g., <code>PDFDocument</code> and <code>WordDocument</code>). If you want to add more document types, you'll have to modify the <code>DocumentViewer</code> class. This creates <strong>tight coupling</strong> between the document types and the view modes, making the code less flexible.</p>

<p><strong>Code Without Bridge Pattern:</strong></p>

```java
interface Document {
    void open();  // Method to open a document
    void renderSinglePage();  // Method to render document in single-page view
    void renderContinuous();  // Method to render document in continuous view
}

class PDFDocument implements Document {
    public void open() {
        System.out.println("Opening PDF document");
    }

    public void renderSinglePage() {
        System.out.println("Rendering PDF in Single Page view");
    }

    public void renderContinuous() {
        System.out.println("Rendering PDF in Continuous view");
    }
}

class WordDocument implements Document {
    public void open() {
        System.out.println("Opening Word document");
    }

    public void renderSinglePage() {
        System.out.println("Rendering Word in Single Page view");
    }

    public void renderContinuous() {
        System.out.println("Rendering Word in Continuous view");
    }
}

class DocumentViewer {
    private PDFDocument pdfDocument;
    private WordDocument wordDocument;

    DocumentViewer(PDFDocument pdfDocument) {
        this.pdfDocument = pdfDocument;
    }

    DocumentViewer(WordDocument wordDocument) {
        this.wordDocument = wordDocument;
    }

    void openDocument() {
        if (pdfDocument != null) pdfDocument.open();
        if (wordDocument != null) wordDocument.open();
    }

    void viewSinglePage() {
        if (pdfDocument != null) pdfDocument.renderSinglePage();
        if (wordDocument != null) wordDocument.renderSinglePage();
    }

    void viewContinuous() {
        if (pdfDocument != null) pdfDocument.renderContinuous();
        if (wordDocument != null) wordDocument.renderContinuous();
    }
}

public class Main {
    public static void main(String[] args) {
        PDFDocument pdf = new PDFDocument();
        DocumentViewer viewer = new DocumentViewer(pdf);
        viewer.openDocument();
        viewer.viewSinglePage();

        WordDocument word = new WordDocument();
        DocumentViewer wordViewer = new DocumentViewer(word);
        wordViewer.openDocument();
        wordViewer.viewContinuous();
    }
}
```

<p><strong>Explanation of Without Bridge Pattern:</strong></p>
<ul>
    <li><strong>Problem:</strong> The <code>DocumentViewer</code> class has separate constructors for each document type (<code>PDFDocument</code> and <code>WordDocument</code>). If you want to add a new document type (e.g., <code>ExcelDocument</code>), you would need to modify the <code>DocumentViewer</code> class.</li>
    <li><strong>Tight Coupling:</strong> The <code>DocumentViewer</code> class directly depends on specific document types. It can't work with new documents without changes.</li>
</ul>

<p><strong>Output:</strong></p>

```java
Opening PDF document
Rendering PDF in Single Page view
Opening Word document
Rendering Word in Continuous view
```

<p><strong>Case 2: With Bridge Pattern (Decoupled)</strong></p>
<p>In this case, we use the <strong>Bridge Pattern</strong> to separate the document type (<code>PDF</code>, <code>Word</code>) from the view mode (<code>SinglePage</code>, <code>Continuous</code>). This decouples the two, allowing for more flexibility. You can add new document types or new view modes without changing the existing code. The <code>DocumentViewer</code> now works with any combination of documents and view modes.</p>

<p><strong>Code With Bridge Pattern:</strong></p>

```java
interface Document {
    void open();  // Method to open a document
}

interface ViewMode {
    void render(Document document);  // Method to render the document in a specific view mode
}

class PDFDocument implements Document {
    public void open() {
        System.out.println("Opening PDF document");
    }
}

class WordDocument implements Document {
    public void open() {
        System.out.println("Opening Word document");
    }
}

class SinglePageView implements ViewMode {
    public void render(Document document) {
        document.open();
        System.out.println("Rendering Single Page View");
    }
}

class ContinuousView implements ViewMode {
    public void render(Document document) {
        document.open();
        System.out.println("Rendering Continuous Page View");
    }
}

class DocumentViewer {
    private Document document;
    private ViewMode viewMode;

    DocumentViewer(Document document, ViewMode viewMode) {
        this.document = document;
        this.viewMode = viewMode;
    }

    void displayDocument() {
        viewMode.render(document);
    }
}

public class Main {
    public static void main(String[] args) {
        Document pdf = new PDFDocument();
        Document word = new WordDocument();

        ViewMode singlePageView = new SinglePageView();
        ViewMode continuousView = new ContinuousView();

        DocumentViewer pdfViewer = new DocumentViewer(pdf, singlePageView);
        pdfViewer.displayDocument();

        DocumentViewer wordViewer = new DocumentViewer(word, continuousView);
        wordViewer.displayDocument();
    }
}
```

<p><strong>Explanation of With Bridge Pattern:</strong></p>
<ul>
    <li><strong>Bridge Pattern Applied:</strong> The <code>Document</code> interface is decoupled from the <code>ViewMode</code> interface. The <code>DocumentViewer</code> takes both <code>Document</code> and <code>ViewMode</code> as parameters and can display any document in any view mode.</li>
    <li><strong>Flexibility:</strong> You can easily add new document types (like <code>ExcelDocument</code>) or new view modes (like <code>ThumbnailView</code>) without changing the existing code. The document and view mode are independent, and you can mix and match them as needed.</li>
</ul>

<p><strong>Output:</strong></p>

```java
Opening PDF document
Rendering Single Page View
Opening Word document
Rendering Continuous Page View
```

<p><strong>Summary of Differences:</strong></p>
<ol>
    <li><strong>Without Bridge Pattern:</strong>
        <ul>
            <li><strong>Tightly Coupled:</strong> <code>DocumentViewer</code> depends on specific document types (like <code>PDFDocument</code> and <code>WordDocument</code>).</li>
            <li><strong>Hard to Extend:</strong> Adding new document types requires changing the <code>DocumentViewer</code> class.</li>
            <li><strong>Limited Flexibility:</strong> You cannot easily change or add new combinations of documents and view modes.</li>
        </ul>
    </li>
    <li><strong>With Bridge Pattern:</strong>
        <ul>
            <li><strong>Decoupled:</strong> The <code>Document</code> and <code>ViewMode</code> are independent of each other.</li>
            <li><strong>Easily Extensible:</strong> New document types or view modes can be added without modifying existing code.</li>
            <li><strong>High Flexibility:</strong> You can mix and match different document types and view modes as needed.</li>
        </ul>
    </li>
</ol>


<p><strong>Real Time Applications</strong></p>
<ul>
    <li><strong>Document Viewer:</strong> Allows opening and rendering different document formats (PDF, Word) in various view modes (single page, continuous) without changing the core logic.</li>
    <li><strong>GUI Frameworks:</strong> Separates the abstraction of UI components (button, textbox) from platform-specific implementations (Windows, macOS).</li>
    <li><strong>Remote Control Systems:</strong> Enables a universal remote control to operate different home appliances (TV, AC) across various brands without modifying the control interface.</li>
    <li><strong>Multimedia Players:</strong> Supports playback of different media formats (MP3, MP4, WAV) with a unified player interface.</li>
    <li><strong>Graphic Rendering Engines:</strong> Renders 3D graphics on different devices (mobile, desktop, VR) while keeping the rendering logic independent of the device.</li>
    <li><strong>Game Development Engines:</strong> Allows games to run across multiple platforms (PC, PlayStation, Xbox) without altering the game logic.</li>
    <li><strong>Cloud Storage Systems:</strong> Provides file operations that work seamlessly across multiple cloud providers (Google Cloud, AWS).</li>
    <li><strong>Database Management Systems (DBMS):</strong> Supports interactions with different databases (MySQL, MongoDB) using the same abstraction for data operations.</li>
</ul>


