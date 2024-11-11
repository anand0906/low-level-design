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
<p>It is a structural design pattern which seperates the abstraction from its implementation, so that both can be developed independently without effecting each other.</p>
<p><strong>How it seperates ?</strong></p>
<ul>
	<li><strong>Abstraction: </strong>This is the high-level part of your system that defines a set of operations or behaviors. It is what the user or the client of your code interacts with. The abstraction does not contain any implementation details; instead, it refers to an implementation</li>
	<li><strong>Implementation: </strong>This is the low-level part that provides the concrete details of how the abstraction’s operations are carried out. The implementation can be easily swapped, modified, or extended without changing the abstraction.</li>
</ul>
<p><strong>Example :</strong></p>

<p>In this example, client is intreracting with abstraction(Device) only.</p>
<p>But the abstraction, always referring the implementation (Mobile,Radio), then only it can access its functionality</p>

```java
interface Device{
    public void turnOn();
    public void turnOff();
}

class Radio implements Device{
    
    @Override
    public void turnOn(){
        System.out.println("Radio : Turning On");
    }

    @Override
    public void turnOff(){
        System.out.println("Radio : Turning Off");
    }
}

class Mobile implements Device{
    
    @Override
    public void turnOn(){
        System.out.println("Mobile : Turning On");
    }

    @Override
    public void turnOff(){
        System.out.println("Mobile : Turning Off");
    }
}

class Client {
    Device device;
    Client(Device device){
        this.device=device;
    }
    
    void Off(){
        this.device.turnOn();
    }
    
    void On(){
        this.device.turnOff();
    }
}


class Main {
    public static void main(String[] args) {
        Client client=new Client(new Radio());
        client.Off();
        client=new Client(new Mobile());
        client.On();
    }
}
```

<p>This is fine when we have simple interface and its implementations</p>
<p>But if there is complex interfaces like as follows</p>

```java
// Online Java Compiler
// Use this editor to write, compile and run your Java code online

interface Device{
    public void turnOn();
    public void turnOff();
}

class Radio implements Device{
    
    @Override
    public void turnOn(){
        System.out.println("Radio : Turning On");
    }

    @Override
    public void turnOff(){
        System.out.println("Radio : Turning Off");
    }
}

class Mobile implements Device{
    
    @Override
    public void turnOn(){
        System.out.println("Mobile : Turning On");
    }

    @Override
    public void turnOff(){
        System.out.println("Mobile : Turning Off");
    }
}

interface Remote{
    void onButton();
    void offButton();
}

class BasicRemoteRadio extends Radio implements Remote{
    
    @Override
    public void onButton(){
        this.turnOn();
    }

    @Override
    public void offButton(){
        this.turnOff();
    }
}

class BasicRemoteMobile extends Mobile implements Remote{
    
    @Override
    public void onButton(){
        this.turnOn();
    }

    @Override
    public void offButton(){
        this.turnOff();
    }
}

class Client {
    Remote remote;
    Client(Remote remote){
        this.remote=remote;
    }
    
    void On(){
        this.remote.onButton();
    }
    
    void Off(){
        this.remote.offButton();
    }
}


class Main {
    public static void main(String[] args) {
        Client client=new Client(new BasicRemoteRadio());
        client.Off();
        client=new Client(new BasicRemoteMobile());
        client.On();
    }
}
```
<p>Here also, Client iteracts with interface (Remote), which is an abstraction which is completely depend on its implementation</p>
<p>Here, the abstraction is littile complex because, the Remote Abstraction depends on Device Implementation to perform its action</p>
<ul>
	<li>Abstraction : Device, Remote</li>
	<li>Remote Depends on Device implementations</li>
</ul>
<p>If we want to implement new abstraction of Remote, it will increase the number of implementation classes exponentially</p>
<p>Suppose we want to add new remote called AdavancedRemote, which will add mute functionality</p>

```java
interface Remote{
    void onButton();
    void offButton();
}

interface AdvancedRemote extends Remote{
    void mute();
}

class BasicRemoteRadio extends Radio implements Remote{
    
    @Override
    public void onButton(){
        this.turnOn();
    }

    @Override
    public void offButton(){
        this.turnOff();
    }
}


class BasicRemoteMobile extends Mobile implements Remote{
    
    @Override
    public void onButton(){
        this.turnOn();
    }

    @Override
    public void offButton(){
        this.turnOff();
    }
}

class AdvancedRemoteMobile extends Mobile implements AdvancedRemote{
    
    @Override
    public void onButton(){
        this.turnOn();
    }

    @Override
    public void offButton(){
        this.turnOff();
    }
    
    @Override
    public void mute(){
        System.out.println("Muting Mobile");
    }
}

class AdvancedRemoteRadio extends Radio implements AdvancedRemote{
    
    @Override
    public void onButton(){
        this.turnOn();
    }

    @Override
    public void offButton(){
        this.turnOff();
    }
    
     @Override
    public void mute(){
        System.out.println("Muting Radio");
    }
}
```
<p>Here we can observe, number of implmentation classes increases exponentially. which will increase complexity</p>
<p>Here, completely tightly coupled with each other (Remote(abstraction) With Devices(Implementations)) which is based on inheritance</p>
<p>Both Remote And Device are independent with each other, remote depends on device to perform opearation</p>
<p>If, there is any scenario, where abstraction and implementations are indepenedent with each other and abstraction depends on implementation, we can use composition instead of inhertance</p>

```java
// Online Java Compiler
// Use this editor to write, compile and run your Java code online

interface Device{
    public void turnOn();
    public void turnOff();
}

class Radio implements Device{
    
    @Override
    public void turnOn(){
        System.out.println("Radio : Turning On");
    }

    @Override
    public void turnOff(){
        System.out.println("Radio : Turning Off");
    }
}

class Mobile implements Device{
    
    @Override
    public void turnOn(){
        System.out.println("Mobile : Turning On");
    }

    @Override
    public void turnOff(){
        System.out.println("Mobile : Turning Off");
    }
}

interface Remote{
    void onButton();
    void offButton();
}

interface AdvancedRemote extends Remote{
    void mute();
}

class BasicRemote implements Remote{
    
    Device device;
    
    BasicRemote(Device device){
        this.device=device;
    }
    
    @Override
    public void onButton(){
        this.device.turnOn();
    }

    @Override
    public void offButton(){
        this.device.turnOff();
    }
}

class AdvancedDeviceRemote implements AdvancedRemote{
    
    Device device;
    
    AdvancedDeviceRemote(Device device){
        this.device=device;
    }
    
    @Override
    public void onButton(){
        this.device.turnOn();
    }

    @Override
    public void offButton(){
        this.device.turnOff();
    }
    
    @Override
    public void mute(){
        System.out.println("Muting Mobile");
    }
}



class Client {
    Remote remote;
    Client(Remote remote){
        this.remote=remote;
    }
    
    void On(){
        this.remote.onButton();
    }
    
    void Off(){
        this.remote.offButton();
    }
}


class Main {
    public static void main(String[] args) {
        Radio radio=new Radio();
        Client client=new Client(new BasicRemote(radio));
        client.Off();
        client=new Client(new AdvancedDeviceRemote(radio));
        client.On();
    }
}
```

<p>Here , we are not depending on client is not completely depending on implementations, instead it depends on abstraction which is holding the implementation of devices, so that easily single abstraction (BasicRemote or AdvancedRemote) can handle multiple devices at run time</p>
<p>This separates the asbtraction (Remote) from implementation (Devices), now both devices and implementations can vary independently</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/Bridge_Design.png">
<p>As shown in image, abstraction holds implementations dynamically, so its looks like bridge, that's why it is called bridge pattern</p>
<ul>
	<li><strong>Abstraction: </strong>Remote</li>
	<li><strong>Refined Abstraction: </strong>AdvnacedRemote</li>
	<li><strong>Implementor: </strong>Device</li>
	<li><strong>Concrete Implmentations: </strong>Radio,Mobile</li>
</ul>

<p><strong>When it can be applied</strong></p>
<p><strong>The Bridge Design Pattern</strong> can be applied in the following situations:</p>

<ol>
    <li>
        <strong>When you have multiple variations of both abstraction and implementation</strong>: 
        <p>If you need to create several variations of an abstraction (like different types of remotes) and several implementations (like different devices), the Bridge pattern helps you avoid creating a large number of classes for every combination.</p>
    </li>
    <li>
        <strong>When you want to avoid a rigid inheritance structure</strong>: 
        <p>If using inheritance to combine abstractions and implementations leads to an explosion of subclasses, the Bridge pattern allows you to use composition instead, making the system more flexible.</p>
    </li>
    <li>
        <strong>When you want to decouple abstraction and implementation</strong>: 
        <p>If you want to change or extend the implementation without modifying the abstraction or vice versa, the Bridge pattern allows both to evolve independently.</p>
    </li>
    <li>
        <strong>When you need flexibility for future extensions</strong>: 
        <p>If you foresee the need to add more abstraction or implementation variations in the future, the Bridge pattern makes it easier to extend without breaking existing code.</p>
    </li>
</ol>

<p>In summary, use the Bridge pattern when you want to decouple abstraction and implementation to allow them to vary independently, especially when both the abstraction and the implementation are likely to change or have many variations.</p>

<p><strong>Use Cases</strong></p>
<ul>
	<li>You have a growing number of classes due to a mix of multiple types of abstractions and implementations, and you want to reduce the complexity.</li>
	<li>You want to keep the abstraction and implementation loosely coupled.</li>
	<li>You need to be able to change either the abstraction or the implementation independently.</li>
	<li>Use if you need to be able to switch implementations at runtime.</li>
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


<h3>Decorator Design Pattern</h3>
<p>It is a structural design pattern that allows to add behaviours/functionalities/responsibilities to existed objects dynamically at runtime without effecting the other objects from the same class.</p>
<p>It is like a alternative way to add additional functionalities using inheritence, which adds functionality at compile time</p>

<p><strong>Use Cases: </strong></p>
<ul>
	<li>Use the Decorator pattern when you need to be able to assign extra behaviors to objects at runtime without breaking the code that uses these objects.</li>
	<li>Use the pattern when it’s not possible to extend an object’s behavior using inheritance.</li>
	<li>When subclassing would result in a large number of subclasses to cover all possible combinations.</li>
	<li>When Core Functionality Should Remain Unchanged: The base object remains unchanged, but its behavior can be altered using decorators.</li>
</ul>

<p><strong>Components: </strong></p>
<ul>
	<li><strong>Component: </strong>It is an abstract class or interface for both the concreate components and decorators</li>
	<li><strong>Concrete Component: </strong>It is implemention of Component. It give the object which we want to add new behaviours at runtime.</li>
	<li><strong>Decorator: </strong>It is a abstract class which implements Component interface and has the refernce to Object which needs additional functionalities</li>
	<li><strong>Concrete Decorator: </strong>These are the concrete classes that extend the Decorator class. They add specific behaviors or responsibilities to the Component. Each Concrete Decorator can add one or more behaviors to the Component.</li>
</ul>

<p><strong>Example: </strong></p>
<p>Suppose we are building a coffee shop application where customers can order different types of coffee. Each coffee can have various optional add-ons such as milk, sugar, whipped cream, etc. We want to implement a system where we can dynamically add these add-ons to a coffee order without modifying the coffee classes themselves.</p>

```java
interface Coffee{
    public String getDescription();
    public Integer cost();
}

class BasicCoffee implements Coffee{

    @Override
    public String getDescription(){
        return "Coffee";
    }
    
    @Override
    public Integer cost(){
        return 100;
    }
}

abstract class CoffeeDecorator implements Coffee{
    Coffee coffee;
    CoffeeDecorator(Coffee coffee){
        this.coffee=coffee;
    }
    
    @Override
    public String getDescription(){
        return this.coffee.getDescription();
    }
    
    @Override
    public Integer cost(){
        return this.coffee.cost();
    }
}

class MilkDecorator extends CoffeeDecorator{
    
    MilkDecorator(Coffee coffee){
        super(coffee);
    }
    
    @Override
    public String getDescription(){
        return this.coffee.getDescription()+",Milk";
    }
    
    @Override
    public Integer cost(){
        return this.coffee.cost()+20;
    }
}

class SugarDecorator extends CoffeeDecorator{
    
    SugarDecorator(Coffee coffee){
        super(coffee);
    }
    
    @Override
    public String getDescription(){
        return this.coffee.getDescription()+",Sugar";
    }
    
    @Override
    public Integer cost(){
        return this.coffee.cost()+20;
    }
}

class Main{
    
    public static void main(String[] args){
        Coffee coffee=new BasicCoffee();
        System.out.println(coffee.getDescription());
        coffee=new MilkDecorator(coffee);
        System.out.println(coffee.getDescription());
        coffee=new SugarDecorator(coffee);
        System.out.println(coffee.getDescription());
    }
    
}
```

<p>Here, we can observe that additional behaviours of sugar , milk is getting added to basic coffee without having any imapact to BasicCoffee implementaion</p>

<p><strong>Real Time Examples</strong></p>
<ul>
	<li><strong>User Interfaces: </strong>Adding scrollbars to text fields, borders to windows, or toolbars to applications without altering the original UI component classes.</li>
	<li><strong>Logging: </strong>Adding logging, security, or notification functionality dynamically to classes.</li>
	<li><strong>Data Processing: </strong> Wrapping data in various decorators to apply filters, formatters, or transformations.</li>
</ul>

<br>
<br>

<h3>Composite Design Pattern</h3>
<p>It is a structural design pattern which allows you to build a structure (Tree) where individual items and group of individual items are treated in the same way.</p>
<p>Think of it like a menu in a restaurant:</p>
<ul>
	<li>A menu can have single items (like "Pasta" or "Salad").</li>
	<li>A menu can also have sub-menus (like "Drinks Menu" with multiple drink options).</li>
</ul>
<p>With the Composite pattern, you can perform the same operations on a single menu item or a whole sub-menu without needing special code for each. For example, you can print the entire menu, and the pattern will handle both individual items and groups seamlessly.</p>

<p><strong>Use Cases: </strong></p>
<ul>
	<li>Use the Composite pattern when you have to implement a tree-like object structure</li>
	<ul>
		<li>The Composite pattern provides you with two basic element types that share a common interface: simple leaves and complex containers. A container can be composed of both leaves and other containers. This lets you construct a nested recursive object structure that resembles a tree.</li>
	</ul>
	<li>Use the pattern when you want the client code to treat both simple and complex elements uniformly.</li>
	<ul>
		<li> All elements defined by the Composite pattern share a common interface. Using this interface, the client doesn’t have to worry about the concrete class of the objects it works with.</li>
	</ul>
	<li>Use when you want to manage complex structures that involve multiple small objects.</li>
</ul>

<p><strong>Components: </strong></p>
<ul>
	<li><strong>Component Interface :</strong>It contains essential methods which needs fo client that should there in both Individual Items (Leaf) and Group of items.</li>
	<li><strong>Leaf (Concrete Component) :</strong>It represents the indivial item ,it doesn't contain any other objects</li>
	<li><strong>Composite (Concrete Component) :</strong>It reprsents the group of items, it is composed of other individual items or group of items</li>
</ul>

```java
import java.util.*;

interface Menu{
    public void setTitle(String title);
    public void print();
}

class MenuItem implements Menu{
    String title;
    
    MenuItem(String title){
        this.title=title;
    }
    
    @Override
    public void setTitle(String title){
        this.title=title;
    }
    
    @Override
    public void print(){
        System.out.println(this.title);
    }
}

class SubMenu implements Menu{
    String title;
    List<Menu> children;
    
    SubMenu(String title){
        this.title=title;
        this.children=new ArrayList<>();
    }
    
    public void addChild(Menu menu){
        this.children.add(menu);
    }
    
    @Override
    public void setTitle(String title){
        this.title=title;
    }
    
    @Override
    public void print(){
        System.out.println(this.title);
        for(Menu item:children){
            item.print();
        }
    }
}

public class Main{
    public static void main(String args[]){
        Menu item1=new MenuItem("Dosa");
        Menu item2=new MenuItem("Idly");
        Menu item3=new MenuItem("Biryani");
        Menu item4=new MenuItem("Meals");
        SubMenu mainMenu=new SubMenu("Main Menu");
        SubMenu tiffens=new SubMenu("Tiffen");
        SubMenu mainCourse=new SubMenu("Main Course");
        tiffens.addChild(item1);
        tiffens.addChild(item2);
        mainCourse.addChild(item3);
        mainCourse.addChild(item4);
        mainMenu.addChild(tiffens);
        mainMenu.addChild(mainCourse);
        System.out.println("printing Main Menu");
        mainMenu.print();
        System.out.println("printing tiffens");
        tiffens.print();
        System.out.println("printing menu item");
        item1.print();
    }
}

```

<p>Your Java code is a great implementation of the <strong>Composite Design Pattern</strong> using a menu example. Here's a brief explanation of how the code demonstrates the pattern:</p>

<p><strong>How This Code Uses the Composite Pattern</strong></p>
<ul>
    <li>
        <strong>Interface (<code>Menu</code>)</strong>: 
        <p>Defines a common interface for both individual items (<code>MenuItem</code>) and groups of items (<code>SubMenu</code>). This allows you to treat both single menu items and sub-menus in a consistent way.</p>
    </li>
    <li>
        <strong>Leaf Class (<code>MenuItem</code>)</strong>: 
        <p>Represents the simplest part of the structure (a single item on the menu). It has a <code>title</code> and a <code>print</code> method to display itself.</p>
    </li>
    <li>
        <strong>Composite Class (<code>SubMenu</code>)</strong>: 
        <p>Represents a group of menu items or sub-menus. It can hold a list of children (<code>List&lt;Menu&gt; children</code>), which could be either <code>MenuItem</code> or <code>SubMenu</code>. The <code>print()</code> method recursively prints all items in the sub-menu.</p>
    </li>
</ul>

<p><strong>Explanation</strong></p>
<ul>
    <li>The <code>Main Menu</code> is a composite structure containing two sub-menus: <code>Tiffen</code> and <code>Main Course</code>.</li>
    <li><code>Tiffen</code> contains two items: <code>Dosa</code> and <code>Idly</code>.</li>
    <li><code>Main Course</code> contains two items: <code>Biryani</code> and <code>Meals</code>.</li>
    <li>The <code>print()</code> method of <code>SubMenu</code> recursively prints its title and all of its children's titles, whether they are individual items or other sub-menus.</li>
</ul>
<p><strong>Benefits</strong></p>
<ul>
    <li><strong>Uniformity</strong>: You can treat individual <code>MenuItem</code> objects and <code>SubMenu</code> objects the same way using the <code>Menu</code> interface.</li>
    <li><strong>Flexibility</strong>: You can easily extend the menu by adding more items or sub-menus.</li>
</ul>

<p>This demonstrates the <strong>Composite Design Pattern</strong> perfectly by allowing both simple and complex objects to be handled uniformly.</p>

<p><strong>Real Time Examples</strong></p>

<p>Here are some real-time examples of the <strong>Composite Design Pattern</strong>:</p>

<ul>
    <li>
        <strong>File System</strong>:
        <p>The file system on your computer is a classic example. You have individual files and folders. A folder can contain both files and other folders, and you can perform operations like open, delete, or move on both in the same way.</p>
    </li>
    <li>
        <strong>Graphical User Interface (GUI)</strong>:
        <p>In GUI frameworks, you have simple components like buttons or text fields and complex components like panels or windows that contain other components. The Composite pattern allows you to treat all components uniformly.</p>
    </li>
    <li>
        <strong>Organization Hierarchy</strong>:
        <p>Companies have organizational structures with different levels: employees, managers, and departments. Each department may contain individual employees or other departments, and operations like calculating the total number of employees can be done uniformly.</p>
    </li>
    <li>
        <strong>Menus in Applications</strong>:
        <p>Menus in software applications (like a drop-down menu) use this pattern. A menu can have individual menu items or sub-menus, and both can be handled uniformly for displaying or activating.</p>
    </li>
    <li>
        <strong>Drawing Applications</strong>:
        <p>In drawing applications (like Photoshop), you have simple shapes like lines or circles and complex shapes composed of several simple shapes. The Composite pattern lets you treat both simple and complex shapes consistently.</p>
    </li>
    <li>
        <strong>Document Structure</strong>:
        <p>In a document editing application, you might have text elements like characters, words, paragraphs, or whole sections. Operations like formatting or searching can be uniformly applied across these different levels.</p>
    </li>
    <li>
        <strong>E-commerce Systems</strong>:
        <p>Product catalogs in an e-commerce system can have individual products and categories that contain multiple products or subcategories. This structure allows you to manage products and categories uniformly.</p>
    </li>
</ul>

<p>These examples illustrate how the Composite Design Pattern helps in managing complex hierarchies and making operations easier to apply across both simple and composite objects.</p>

<h3>Fascade Design Pattern</h3>
<p>It is a structural design pattern that provides a simple interface which hides all complexity involved in using other classes or subsystems to peform operation, so the client can interact with just the interface instead of dealing with the complexity of multiple classes or subsystems.</p>

<p><strong>Use Cases: </strong></p>
<ul>
	<li><strong>To Hide Complexity :</strong>When you have a complex system with many interdependent classes and you want to provide a simpler interface.</li>
	<li><strong>To Make Code More Manageable :</strong>When you want to keep the code organized by reducing dependencies.</li>
	<li><strong>When Upgrading or Expanding Systems :</strong>t’s useful when you’re expanding or upgrading a system, as you can make changes behind the facade without impacting the client.</li>
</ul>

<p><strong>Example :</strong></p>

```java
// Complex subsystems
class Engine {
    public void start() {
        System.out.println("Engine started.");
    }
}

class FuelPump {
    public void pump() {
        System.out.println("Fuel pump activated.");
    }
}

class Battery {
    public void providePower() {
        System.out.println("Battery providing power.");
    }
}

// Facade
class CarFacade {
    private Engine engine;
    private FuelPump fuelPump;
    private Battery battery;

    public CarFacade() {
        engine = new Engine();
        fuelPump = new FuelPump();
        battery = new Battery();
    }

    public void startCar() {
        battery.providePower();
        fuelPump.pump();
        engine.start();
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        CarFacade car = new CarFacade();
        car.startCar(); // Start the car using the facade
    }
}
```

<p>Here, CarFacade simplifies the process of starting the car by providing a start_car method that handles all the details internally.</p>

```java
// Complex subsystems
class Amplifier {
    public void on() {
        System.out.println("Amplifier on.");
    }

    public void setVolume(int level) {
        System.out.println("Amplifier volume set to " + level);
    }
}

class DVDPlayer {
    public void on() {
        System.out.println("DVD Player on.");
    }

    public void play(String movie) {
        System.out.println("Playing '" + movie + "'");
    }
}

class Projector {
    public void on() {
        System.out.println("Projector on.");
    }

    public void wideScreenMode() {
        System.out.println("Projector in widescreen mode.");
    }
}

// Facade
class HomeTheaterFacade {
    private Amplifier amp;
    private DVDPlayer dvd;
    private Projector projector;

    public HomeTheaterFacade(Amplifier amp, DVDPlayer dvd, Projector projector) {
        this.amp = amp;
        this.dvd = dvd;
        this.projector = projector;
    }

    public void watchMovie(String movie) {
        System.out.println("Get ready to watch a movie...");
        amp.on();
        amp.setVolume(5);
        dvd.on();
        dvd.play(movie);
        projector.on();
        projector.wideScreenMode();
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        Amplifier amp = new Amplifier();
        DVDPlayer dvd = new DVDPlayer();
        Projector projector = new Projector();
        HomeTheaterFacade homeTheater = new HomeTheaterFacade(amp, dvd, projector);

        homeTheater.watchMovie("Inception"); // Watch the movie using the facade
    }
}
```

<p>In this example, the HomeTheaterFacade simplifies the process of setting up the home theater system, allowing the user to call a single watch_movie method.</p>


<h3>FlyWeight Design Pattern</h3>
<p>It is a structural design pattern that reduces memory usage by reusing objects with similar data. Instead of creating new instances every time, it stores shared objects in a central repository (shared memory). When a new object is requested, the system checks if an identical object already exists in the shared memory. If it does, it returns the existing object; if not, it creates a new one.</p>

<p><strong>Use Cases : </strong></p>
<ul>
    <li>When there are a large number of similar objects that can share data (e.g., multiple shapes in a graphic editor).</li>
    <li>When memory usage is a concern, and objects have some attributes that can be shared.</li>
    <li>When the cost of creating new objects is high, and object reuse can optimize performance.</li>
</ul>

<p><strong>Example : </strong></p>

```java
import java.util.HashMap;
import java.util.Map;

// Flyweight interface
interface Shape {
    void draw(String color);
}

// Concrete Flyweight
class Circle implements Shape {
    private String color; // intrinsic state
    
    // constructor to set the color for the circle
    public Circle(String color) {
        this.color = color;
    }

    @Override
    public void draw(String color) {
        // Use the color passed for the extrinsic state
        System.out.println("Drawing circle of color: " + color + " and shared color: " + this.color);
    }
}

// Flyweight Factory
class ShapeFactory {
    private Map<String, Shape> circleMap = new HashMap<>();
    
    public Shape getCircle(String color) {
        Shape circle = circleMap.get(color);
        
        if (circle == null) {
            circle = new Circle(color);
            circleMap.put(color, circle);
            System.out.println("Creating circle of color: " + color);
        }
        
        return circle;
    }
}

// Client Code
public class FlyweightExample {
    public static void main(String[] args) {
        ShapeFactory shapeFactory = new ShapeFactory();
        
        // Shared shapes
        Shape circle1 = shapeFactory.getCircle("Red");
        Shape circle2 = shapeFactory.getCircle("Blue");
        
        // Extrinsic state differs
        circle1.draw("X");
        circle2.draw("Y");
        
        // Reusing existing circle object
        Shape circle3 = shapeFactory.getCircle("Red");
        circle3.draw("Z");
    }
}
```

<p>The ShapeFactory creates only one circle object per unique color, and subsequent requests for that color reuse the existing object.</p>
<p>The intrinsic state (color) is shared among the objects, while the extrinsic state (X, Y, Z) is passed when calling the draw() method.</p>

<h3>Proxy Design Pattern</h3>
<p>It is a structural design patten that provides an object (Proxy) which represents the another object(Real), where proxy acts as helper for real object,that ontrols access to the real object by adding additional functionality like access control, logging, lazy initialization, etc., without changing the real object itself.</p>

<p><strong>Use Cases : </strong></p>
<p><strong>Use Cases for Proxy Design Pattern</strong></p>

<ol>
    <li>
        <p><strong>Lazy Initialization (Virtual Proxy):</strong></p>
        <ul>
            <li>Use when an object is expensive to create, and you want to delay its creation until it's needed.</li>
            <li>Example: A large image or a complex report is not loaded until the user requests it.</li>
        </ul>
    </li>
    <li>
        <p><strong>Access Control (Protection Proxy):</strong></p>
        <ul>
            <li>Use when you want to control access to an object based on permissions or conditions.</li>
            <li>Example: Restricting access to a resource or service based on user roles (admin, guest, etc.).</li>
        </ul>
    </li>
    <li>
        <p><strong>Remote Access (Remote Proxy):</strong></p>
        <ul>
            <li>Use when an object exists in a different address space (such as another machine or network), and you need a proxy to interact with it.</li>
            <li>Example: Communicating with a remote server or database over the network.</li>
        </ul>
    </li>
    <li>
        <p><strong>Caching (Cache Proxy):</strong></p>
        <ul>
            <li>Use when you want to store a local copy of an object to avoid recalculating or reloading it multiple times.</li>
            <li>Example: Storing results of expensive calculations or data fetched from a database to speed up future access.</li>
        </ul>
    </li>
    <li>
        <p><strong>Monitoring (Smart Proxy):</strong></p>
        <ul>
            <li>Use when you want to monitor the usage of an object, like counting the number of times an object is accessed or logging activity.</li>
            <li>Example: Counting the number of times a database connection is used or logging each method call for debugging.</li>
        </ul>
    </li>
    <li>
        <p><strong>Preloading (Virtual Proxy):</strong></p>
        <ul>
            <li>Use when you want to preload certain data or resources before the user actually needs them.</li>
            <li>Example: Preloading game assets or web page content to enhance performance.</li>
        </ul>
    </li>
</ol>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Subject Interface</strong>: Defines the common interface for the real object and the proxy.</li>
    <li><strong>Real Subject</strong>: The actual object that the proxy represents.</li>
    <li><strong>Proxy</strong>: The proxy class that implements the subject interface and holds a reference to the real subject, controlling access to it.</li>
</ol>


<p><strong>Example : </strong></p>

```java
// Subject Interface
interface Subject {
    void performAction();
}

// Real Subject
class RealSubject implements Subject {
    @Override
    public void performAction() {
        System.out.println("Action performed by RealSubject.");
    }
}

// Proxy
class Proxy implements Subject {
    private RealSubject realSubject;

    @Override
    public void performAction() {
        if (realSubject == null) {
            realSubject = new RealSubject();  // Lazy initialization
        }
        realSubject.performAction();
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        Subject proxy = new Proxy();
        proxy.performAction(); // The real subject is initialized only when needed
    }
}
```

<p><strong>Real Time Examples</strong></p>
<p><strong>1. Virtual Proxy:</strong></p>
<ul>
    <li><strong>Example:</strong> Image loading in a photo gallery app.</li>
    <li><strong>Explanation:</strong> When displaying a large collection of images, instead of loading all images at once, the proxy can load a placeholder image first and load the actual image only when the user views it. This reduces memory usage and loading time.</li>
</ul>

<p><strong>2. Remote Proxy:</strong></p>
<ul>
    <li><strong>Example:</strong> Database access or remote service call.</li>
    <li><strong>Explanation:</strong> When accessing a remote database or a web service, a proxy can be used to handle communication between the client and the server. It handles network issues, retries, and can also provide local caching of data to optimize performance.</li>
</ul>

<p><strong>3. Protection Proxy:</strong></p>
<ul>
    <li><strong>Example:</strong> File access control.</li>
    <li><strong>Explanation:</strong> In a system with multiple users, a proxy can be used to restrict access to certain files or resources. The proxy checks the user’s permissions before forwarding the request to the real resource. For instance, an admin user may have access to sensitive data, whereas regular users do not.</li>
</ul>

<p><strong>4. Cache Proxy:</strong></p>
<ul>
    <li><strong>Example:</strong> Caching API responses.</li>
    <li><strong>Explanation:</strong> When making API calls to fetch data that doesn't change frequently, a proxy can store (cache) the responses. The next time the same data is requested, the proxy can return the cached response, reducing the need for repeated API calls and improving performance.</li>
</ul>

<p><strong>5. Smart Proxy:</strong></p>
<ul>
    <li><strong>Example:</strong> Memory management in large systems.</li>
    <li><strong>Explanation:</strong> In a system where objects consume a lot of memory (like a game with complex 3D models), a smart proxy can be used to load objects into memory only when necessary and unload them when they are no longer in use. This prevents unnecessary memory consumption.</li>
</ul>

<p><strong>6. Firewall Proxy:</strong></p>
<ul>
    <li><strong>Example:</strong> Security and network filtering.</li>
    <li><strong>Explanation:</strong> A proxy server can act as an intermediary between a user and the internet, filtering requests for malicious content or blocking access to certain websites based on company policies.</li>
</ul>

<p><strong>7. Internet Proxy (Browser Proxy):</strong></p>
<ul>
    <li><strong>Example:</strong> Web browsers accessing the internet.</li>
    <li><strong>Explanation:</strong> A proxy server sits between a client (web browser) and the internet to handle requests, possibly caching content or providing additional security features like encryption, monitoring, and logging.</li>
</ul>

<p><strong>8. Logging Proxy:</strong></p>
<ul>
    <li><strong>Example:</strong> API request logging.</li>
    <li><strong>Explanation:</strong> A proxy can be used to intercept method calls to the real object and log the details of each method invocation (e.g., time, parameters, results). This is useful for debugging and monitoring system performance.</li>
</ul>

<p><strong>9. Lazy Initialization Proxy:</strong></p>
<ul>
    <li><strong>Example:</strong> User authentication systems.</li>
    <li><strong>Explanation:</strong> In some systems, a user’s profile data might be loaded only when needed. For example, a proxy can be used to delay the loading of detailed user data (like profile picture, preferences) until the user actually requests it.</li>
</ul>

<p><strong>10. Multimedia Streaming:</strong></p>
<ul>
    <li><strong>Example:</strong> Streaming media services like Netflix or YouTube.</li>
    <li><strong>Explanation:</strong> A proxy could be used to handle buffering, load balancing, or security when delivering media content from a server to the client. It can help improve streaming performance or provide caching to reduce bandwidth usage.</li>
</ul>

<p><strong>11. Cloud Services Access:</strong></p>
<ul>
    <li><strong>Example:</strong> Using a proxy to access cloud storage.</li>
    <li><strong>Explanation:</strong> In cloud environments, proxies are often used to provide access control, logging, and monitoring for requests made to cloud services like AWS, Google Cloud, or Azure. They can help ensure proper authentication and security while also enabling logging of user activity.</li>
</ul>

