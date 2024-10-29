<h1>Design Principles</h1>
<p>Design principles in software development are guidelines that help developers create software that’s easy to understand, maintain, and extend over time. They are like the "rules of the road" for programming, making sure that the code is clear, efficient, and adaptable</p>
<p>Here are some key design principles</p>
<ul>
	<li><strong>SOLID</strong></li>
	<li><strong>DRY</strong></li>
	<li><strong>KISS</strong></li>
	<li><strong>YAGNI</strong></li>
	<li><strong>Separation Of Concerns</strong></li>
	<li><strong>Modularity</strong></li>
</ul>

<h2>SOLID</h2>
<p>SOLID is a set of guidelines to make object oriented programming better and easier to manage. These principles help programmers write code that is organized, easy to update and extensible.</p>
<p>The SOLID principles were first introduced by the famous Computer Scientist Robert J. Martin (a.k.a Uncle Bob) in his paper in 2000. But the SOLID acronym was introduced later by Michael Feathers.</p>
<p>These guidelines mostly focuses on</p>
<ul>
	<li>Organizing Code Into Clear Parts</li>
	<li>Deciding What To Show and What To Hide</li>
	<li>How Different Parts Of Code Works Together</li>
</ul>
<p>Overall, SOLID principles help developers write code that’s easy to organize, safe to update, and flexible enough to adapt to new needs.</p>
<p>To make this as simple to follow, I will be using the word “Class” but note that it can also apply to a Function, Method or Module in this article.</p>
<p><strong>SOLID</strong> is acronym which stands for</p>
<ol>
	<li><strong>S :</strong>Single Responsiblity Principle</li>
	<li><strong>O :</strong>Open-Closed Principle</li>
	<li><strong>L :</strong>Liskov Substitution Principle</li>
	<li><strong>I :</strong>Interface Seggregation Principle</li>
	<li><strong>D :</strong>Dependency Inversion Principle</li>
</ol>

<h3>Single Responsiblity Principle</h3>
<p>The Single Responsibility Principle (SRP) states that every class or module should have only one reason to change, meaning it should only perform one specific task or responsibility. </p>
<i>A class should have a single responsibility</i>
<img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*P3oONz9Da3Tc1w97fMV73Q.png">
<p>If a Class has many responsibilities, it increases the possibility of bugs because making changes to one of its responsibilities, could affect the other ones without you knowing.</p>
<p><strong>Single Responsibility Principle (SRP)</strong> states that every class or module should have only one reason to change, meaning it should only perform one specific task or responsibility. In simpler terms, each class should focus on doing just one job. This principle keeps code cleaner and easier to maintain.</p>

<p><strong>Example Without SRP</strong></p>

<p>Here’s an example of an <code>Invoice</code> class that does multiple things:</p>

```java
public class Invoice {
    private double subtotal;
    private double tax;

    public Invoice(double subtotal, double tax) {
        this.subtotal = subtotal;
        this.tax = tax;
    }

    // Method to calculate the total amount of the invoice
    public double calculateTotal() {
        return subtotal + tax;
    }

    // Method to print the invoice details
    public void printInvoice() {
        System.out.println("Invoice Details:");
        System.out.println("Subtotal: " + subtotal);
        System.out.println("Tax: " + tax);
        System.out.println("Total: " + calculateTotal());
    }

    // Method to save the invoice details to a database
    public void saveToDatabase() {
        System.out.println("Saving invoice to the database...");
    }
}
```

<p>This <code>Invoice</code> class violates SRP because:</p>
<ul>
    <li>It calculates totals (<code>calculateTotal()</code>).</li>
    <li>It prints the invoice (<code>printInvoice()</code>).</li>
    <li>It saves to a database (<code>saveToDatabase()</code>).</li>
</ul>

<p>Now let’s apply SRP by creating separate classes:</p>

<p><strong>1. The Invoice Class</strong></p>
<p>This class will now only contain the data related to the invoice, acting as a <em>data model</em>.</p>

```java
public class Invoice {
    private double subtotal;
    private double tax;

    public Invoice(double subtotal, double tax) {
        this.subtotal = subtotal;
        this.tax = tax;
    }

    public double getSubtotal() {
        return subtotal;
    }

    public double getTax() {
        return tax;
    }
}
```

<p><strong>2. The InvoiceCalculator Class</strong></p>
<p>This class is responsible for calculating the total amount of the invoice.</p>

```java
public class InvoiceCalculator {
    public double calculateTotal(Invoice invoice) {
        return invoice.getSubtotal() + invoice.getTax();
    }
}
```

<p><strong>3. The InvoicePrinter Class</strong></p>
<p>This class handles the responsibility of printing the invoice details.</p>

```java
public class InvoicePrinter {
    public void printInvoice(Invoice invoice, InvoiceCalculator calculator) {
        System.out.println("Invoice Details:");
        System.out.println("Subtotal: " + invoice.getSubtotal());
        System.out.println("Tax: " + invoice.getTax());
        System.out.println("Total: " + calculator.calculateTotal(invoice));
    }
}
```

<p><strong>4. The InvoiceSaver Class</strong></p>
<p>This class is responsible for saving the invoice data to the database.</p>

```java
public class InvoiceSaver {
    public void saveToDatabase(Invoice invoice) {
        System.out.println("Saving invoice to the database...");
        // Database saving logic here
    }
}
```

<p><strong>Using the SRP Classes Together</strong></p>

```java
public class Main {
    public static void main(String[] args) {
        Invoice invoice = new Invoice(100.0, 15.0);
        InvoiceCalculator calculator = new InvoiceCalculator();
        InvoicePrinter printer = new InvoicePrinter();
        InvoiceSaver saver = new InvoiceSaver();

        // Calculate and print the invoice
        printer.printInvoice(invoice, calculator);

        // Save the invoice to the database
        saver.saveToDatabase(invoice);
    }
}
```

<p><strong>Advantages :</strong></p>
<ol>
	<li><strong>Easier Maintenance:</strong></li>
	<p>When a class does only one job, updating or fixing it becomes much easier. You know exactly where to look if there’s a problem or if you need to change something related to that responsibility.</p>
	<li><strong>Improved Readability:</strong></li>
	<p>Code becomes easier to read and understand when each class has a clear, single responsibility. Other developers (and even your future self) can quickly understand what each part does.</p>
	<li><strong>Reduced Risk of Bugs/Merge Conflicts:</strong></li>
	<p>If each class does just one thing, changes to one class are less likely to affect others. This reduces the chance of introducing bugs in unrelated parts of the code.</p>
	<li><strong>Easier Testing:</strong></li>
	<p>Testing is simpler when a class has one responsibility, as you’re only verifying one thing. This makes it easier to write targeted, effective tests.</p>
	<li><strong>Supports Code Reuse:</strong></li>
	<p>Classes that focus on one task can be reused in different projects or parts of the program since they’re not tied to other responsibilities.</p>
</ol>

<h3>Open-Closed Principle</h3>
<p><strong>Open-Closed Principle (OCP)</strong> states that software entities like classes, modules, and functions should be <strong>open for extension but closed for modification</strong>. This means you should be able to add new functionality to a class without changing its existing code.</p>

<p>The main idea is to avoid modifying existing code to prevent bugs and keep the system stable. Instead, you can add new features by creating new classes or methods, extending the current behavior without altering what already exists.</p>

<p><strong>Key Points of the Open-Closed Principle</strong></p>
<ol>
    <li><strong>Open for Extension:</strong> You can add new features or behaviors by extending the existing code.</li>
    <li><strong>Closed for Modification:</strong> The existing code should remain untouched and stable.</li>
</ol>

<img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*0MtFBmm6L2WVM04qCJOZPQ.png">

<p>Changing the current behaviour of a Class will affect all the systems using that Class.</p>
<p>If you want the Class to perform more functions, the ideal approach is to add to the functions that already exist NOT change them.</p>
<p>This principle aims to extend a Class’s behaviour without changing the existing behaviour of that Class. This is to avoid causing bugs wherever the Class is being used.</p>

<p><strong>Advantages of the Open-Closed Principle for Developers</strong></p>
<ol>
    <li><strong>Reduces Bugs:</strong> By not modifying existing code, you avoid introducing new bugs into tested and stable code.</li>
    <li><strong>Easier Maintenance:</strong> Each change or addition is isolated, making the system easier to maintain and understand.</li>
    <li><strong>Better for Team Collaboration:</strong> Multiple developers can work on adding features without worrying about breaking or conflicting with each other’s code.</li>
    <li><strong>Scalability:</strong> Systems designed with OCP are more adaptable to future changes, making them scalable and flexible.</li>
</ol>

<p>But how are we going to add new functionality without touching the class, you may ask. It is usually done with the help of interfaces and abstract classes.</p>

<p><strong>Example of Open-Closed Principle in Java</strong></p>

<p>Let’s take an example of a <code>Shape</code> interface and create different shapes with an <code>AreaCalculator</code> class that calculates the area of any shape.</p>

<p><strong>Without Applying OCP</strong></p>

<p>Suppose we start by creating an <code>AreaCalculator</code> class that can only calculate the area of a circle. Later, if we want to add support for new shapes (like rectangles or triangles), we would need to modify the <code>AreaCalculator</code> class to handle each new shape. This approach violates OCP because each new shape requires modifying the <code>AreaCalculator</code> class.</p>

```java
class Circle {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    public double getRadius() {
        return radius;
    }
}

class AreaCalculator {
    public double calculateCircleArea(Circle circle) {
        return Math.PI * circle.getRadius() * circle.getRadius();
    }
}
```

<p>If we need to calculate the area of a <code>Rectangle</code>, we’d need to modify <code>AreaCalculator</code> to add a new method, which violates OCP.</p>

<p><strong>Applying OCP: Extending Instead of Modifying</strong></p>

<p>To follow OCP, we can create a <code>Shape</code> interface that each shape will implement. Then, we modify <code>AreaCalculator</code> to work with any class that implements <code>Shape</code>. This way, we can add new shapes in the future without changing <code>AreaCalculator</code>.</p>

<p><strong>1. Define the Shape Interface</strong></p>

```java
interface Shape {
    double calculateArea();
}
```

<p><strong>2. Create Implementations of Different Shapes</strong></p>

```java
class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }
}
```

<p><strong>3. Update AreaCalculator to Use Shape Interface</strong></p>

```java
class AreaCalculator {
    public double calculateArea(Shape shape) {
        return shape.calculateArea();
    }
}
```

<p><strong>4. Usage</strong></p>

```java
public class Main {
    public static void main(String[] args) {
        Circle circle = new Circle(5);
        Rectangle rectangle = new Rectangle(4, 6);
        AreaCalculator calculator = new AreaCalculator();

        System.out.println("Circle Area: " + calculator.calculateArea(circle));
        System.out.println("Rectangle Area: " + calculator.calculateArea(rectangle));
    }
}

```

<p><strong>How This Follows OCP</strong></p>
<ol>
    <li><strong>Adding New Shapes:</strong> If we want to add a <code>Triangle</code> or any other shape, we just need to create a new class that implements the <code>Shape</code> interface. The <code>AreaCalculator</code> class doesn’t need to be changed.</li>
    <li><strong>Flexible and Extendable:</strong> The system is flexible and ready for future extensions, as we can add new shapes without modifying the <code>AreaCalculator</code> class, following the Open-Closed Principle perfectly.</li>
</ol>

<p>By following OCP, we make our code more robust, flexible, and easy to extend without the risk of breaking existing functionality.</p>

<h3>Liskov Substitution Principle</h3>
<p><strong>Liskov Substitution Principle (LSP)</strong>states that objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program. In simpler terms, if you have a class (the parent or base class) and a subclass (derived class), you should be able to use the subclass wherever you use the superclass without any issues.</p>

<img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*yKk2XKJaCLNlDxQMx1r55Q.png">

<p><strong>Key Points of the Liskov Substitution Principle</strong></p>
<ol>
    <li><strong>Behavioral Consistency:</strong> Subclasses should fulfill the expected behavior of the superclass. If a method in the superclass is called, it should work the same way with a subclass instance.</li>
    <li><strong>Contract Adherence:</strong> A subclass should adhere to the contract established by the superclass. This includes:
        <ul>
            <li>Maintaining the input and output types.</li>
            <li>Not introducing new constraints that the superclass does not have.</li>
            <li>Providing the same functionality and ensuring that clients can rely on the subclass.</li>
        </ul>
    </li>
    <li><strong>Invariant Conditions:</strong> Subclasses should not violate the invariants of the superclass. If the superclass has certain conditions that must always be true, the subclass should not invalidate them.</li>
</ol>

<p>This principle aims to enforce consistency so that the parent Class or its child Class can be used in the same way without any errors.</p>

<p><strong>Advantages of Liskov Substitution Principle</strong></p>
<ol>
    <li><strong>Enhanced Code Reusability:</strong> By adhering to LSP, you can substitute subclasses for their base classes, enhancing code reusability and flexibility.</li>
    <li><strong>Improved Maintainability:</strong> Code is easier to maintain because you can expect subclasses to behave consistently with the base class, reducing surprises when you make substitutions.</li>
    <li><strong>Better Testing:</strong> You can test code with base class references and substitute different subclasses, ensuring that the behavior remains consistent.</li>
</ol>

<p><strong>Example of Liskov Substitution Principle in Java</strong></p>

<p>Let’s consider an example involving a class hierarchy of shapes, specifically focusing on rectangles and squares.</p>

<p><strong>Without Applying LSP</strong></p>

<p>Suppose we have a base class <code>Rectangle</code> and a subclass <code>Square</code>. The <code>Rectangle</code> class has methods to set width and height. However, a square has equal width and height. If we don’t adhere to LSP, using a <code>Square</code> in place of a <code>Rectangle</code> can lead to unexpected behavior.</p>

```java
class Rectangle {
    private double width;
    private double height;

    public void setWidth(double width) {
        this.width = width;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    public double getArea() {
        return width * height;
    }
}

class Square extends Rectangle {
    @Override
    public void setWidth(double width) {
        super.setWidth(width);
        super.setHeight(width); // Height should also be set to the same value
    }

    @Override
    public void setHeight(double height) {
        super.setHeight(height);
        super.setWidth(height); // Width should also be set to the same value
    }
}
```

<p>Here, substituting a <code>Square</code> for a <code>Rectangle</code> can cause issues. If you set the width of a rectangle and expect to get a different height, using a <code>Square</code> will not provide the expected behavior.</p>

<p><strong>Applying LSP</strong></p>

<p>To adhere to LSP, we can modify our design. Instead of having <code>Square</code> inherit from <code>Rectangle</code>, we can create a separate class hierarchy where both <code>Square</code> and <code>Rectangle</code> implement a common interface, such as <code>Shape</code>.</p>

<p><strong>1. Define a Shape Interface</strong></p>

```java
interface Shape {
    double getArea();
}
```

<p><strong>2. Implement Rectangle and Square Classes</strong></p>

```java
class Rectangle implements Shape {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    public double getArea() {
        return width * height;
    }
}

class Square implements Shape {
    private double side;

    public Square(double side) {
        this.side = side;
    }

    public double getArea() {
        return side * side;
    }
}
```

<p><strong>3. Usage</strong></p>

```java
public class Main {
    public static void main(String[] args) {
        Shape rectangle = new Rectangle(4, 5);
        Shape square = new Square(4);

        System.out.println("Rectangle Area: " + rectangle.getArea());
        System.out.println("Square Area: " + square.getArea());
    }
}
```

<p><strong>How This Follows LSP</strong></p>
<ol>
    <li><strong>Consistent Behavior:</strong> Both <code>Rectangle</code> and <code>Square</code> implement the <code>Shape</code> interface and provide the same method (<code>getArea()</code>). Substituting one for the other will not break the expected behavior.</li>
    <li><strong>No Surprises:</strong> When you use a <code>Shape</code> reference, you can confidently call <code>getArea()</code> without worrying about how each shape is implemented internally. This maintains the integrity of the program.</li>
</ol>

<p>By adhering to the Liskov Substitution Principle, we ensure that our subclasses can be used interchangeably with their parent classes without causing errors or unexpected behaviors. This leads to a more robust and maintainable codebase.</p>


<h3>Interface Segregation Principle</h3>
<p><strong>Interface Segregation Principle (ISP)</strong>states that no client should be forced to depend on methods it does not use. In simpler terms, interfaces should be specific to the clients that use them rather than being general-purpose and forcing clients to implement methods that may not be relevant to them.</p>

<img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*2hmyR9L43Vm64MYxj4Y89w.png">

<p>This principle aims at splitting a set of actions into smaller sets so that a Class executes ONLY the set of actions it require</p>

<p>When a Class is required to perform actions that are not useful, it is wasteful and may produce unexpected bugs if the Class does not have the ability to perform those actions.</p>

<p>A Class should perform only actions that are needed to fulfil its role. Any other action should be removed completely or moved somewhere else if it might be used by another Class in the future.</p>

<p><strong>Key Points of the Interface Segregation Principle</strong></p>
<ol>
    <li><strong>Client-Specific Interfaces:</strong> Create interfaces that are tailored to the needs of specific clients. This reduces unnecessary dependencies and makes the code more maintainable.</li>
    <li><strong>Avoid Fat Interfaces:</strong> A "fat" interface is one that has too many methods, some of which may not be applicable to all implementing classes. Instead of a large interface, it’s better to break it down into smaller, more focused interfaces.</li>
    <li><strong>Promotes Flexibility:</strong> By keeping interfaces small and focused, the code becomes more flexible and easier to modify. Changes in one interface won’t affect unrelated clients.</li>
    <li><strong>Improves Code Readability:</strong> Smaller interfaces improve readability and understanding since clients only need to consider the methods that are relevant to them.</li>
</ol>

<p><strong>Advantages of the Interface Segregation Principle</strong></p>
<ol>
    <li><strong>Reduced Impact of Changes:</strong> When interfaces change, the impact on clients is minimized because only the clients that use those specific methods are affected.</li>
    <li><strong>Enhanced Maintainability:</strong> Smaller, focused interfaces make the codebase easier to maintain and extend over time.</li>
    <li><strong>Improved Testability:</strong> It’s easier to write tests for smaller interfaces, as you can create mock implementations that only include the necessary methods.</li>
</ol>

<p><strong>Example of Interface Segregation Principle in Java</strong></p>

<p>Let’s consider an example of a media player that can play different types of media. If we create a single, large interface for all media types, it may include methods that not all clients need.</p>

<p><strong>Without Applying ISP</strong></p>

<p>Suppose we have a large interface <code>MediaPlayer</code> that includes methods for playing and recording audio and video.</p>

```java
interface MediaPlayer {
    void playAudio(String audioFile);
    void playVideo(String videoFile);
    void recordAudio(String audioFile);
    void recordVideo(String videoFile);
}

class AudioPlayer implements MediaPlayer {
    @Override
    public void playAudio(String audioFile) {
        System.out.println("Playing audio: " + audioFile);
    }

    @Override
    public void playVideo(String videoFile) {
        throw new UnsupportedOperationException("AudioPlayer cannot play video.");
    }

    @Override
    public void recordAudio(String audioFile) {
        System.out.println("Recording audio: " + audioFile);
    }

    @Override
    public void recordVideo(String videoFile) {
        throw new UnsupportedOperationException("AudioPlayer cannot record video.");
    }
}
```

<p>In this case, the <code>AudioPlayer</code> class implements all methods of the <code>MediaPlayer</code> interface, but it only needs to use <code>playAudio</code> and <code>recordAudio</code>. The other methods are irrelevant, leading to unnecessary implementation and potential runtime errors.</p>

<p><strong>Applying ISP</strong></p>

<p>To adhere to the Interface Segregation Principle, we can break the large <code>MediaPlayer</code> interface into smaller, more specific interfaces.</p>

<p><strong>1. Define Smaller Interfaces</strong></p>

```java
interface AudioPlayer {
    void playAudio(String audioFile);
    void recordAudio(String audioFile);
}

interface VideoPlayer {
    void playVideo(String videoFile);
    void recordVideo(String videoFile);
}
```

<p><strong>2. Implement Specific Interfaces</strong></p>

```java
class SimpleAudioPlayer implements AudioPlayer {
    @Override
    public void playAudio(String audioFile) {
        System.out.println("Playing audio: " + audioFile);
    }

    @Override
    public void recordAudio(String audioFile) {
        System.out.println("Recording audio: " + audioFile);
    }
}

class SimpleVideoPlayer implements VideoPlayer {
    @Override
    public void playVideo(String videoFile) {
        System.out.println("Playing video: " + videoFile);
    }

    @Override
    public void recordVideo(String videoFile) {
        System.out.println("Recording video: " + videoFile);
    }
}
```

<p><strong>3. Usage</strong></p>

```java
public class Main {
    public static void main(String[] args) {
        AudioPlayer audioPlayer = new SimpleAudioPlayer();
        audioPlayer.playAudio("song.mp3");
        audioPlayer.recordAudio("voice.mp3");

        VideoPlayer videoPlayer = new SimpleVideoPlayer();
        videoPlayer.playVideo("movie.mp4");
        videoPlayer.recordVideo("clip.mp4");
    }
}
```

<p><strong>How This Follows ISP</strong></p>
<ol>
    <li><strong>Client-Specific Interfaces:</strong> Each player class now implements only the methods relevant to them. The <code>AudioPlayer</code> class does not implement any video-related methods, which avoids unnecessary complexity.</li>
    <li><strong>No Unused Methods:</strong> Clients are no longer forced to implement methods that are not applicable to them. This leads to cleaner, more understandable code.</li>
    <li><strong>Flexibility and Maintenance:</strong> If you decide to add new features or change existing ones, you can do so without impacting other unrelated classes. This makes the system easier to maintain and extend.</li>
</ol>

<p>By adhering to the Interface Segregation Principle, we ensure that our interfaces are more focused and relevant to their clients, leading to a cleaner, more maintainable codebase.</p>


<h3>Dependency Inversion Principle</h3>
<p><strong>Dependency Inversion Principle (DIP)</strong> states that high-level modules should not depend on low-level modules; both should depend on abstractions. Additionally, abstractions should not depend on details, but details should depend on abstractions.</p>

<p>The Dependency Inversion principle states that our classes should depend upon interfaces or abstract classes instead of concrete classes and functions.</p>

<p>In simpler terms, this principle suggests that instead of having your code directly depend on specific implementations, you should depend on interfaces or abstract classes. This leads to a more flexible and maintainable design.</p>

<img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*Qk8tDmjQlyvwKxNTfXIo0Q.png">

<p>Firstly, let’s define the terms used here more simply</p>
<p>High-level Module(or Class): Class that executes an action with a tool.</p>
<p>Low-level Module (or Class): The tool that is needed to execute the action</p>
<p>Abstraction: Represents an interface that connects the two Classes.</p>
<p>Details: How the tool works</p>
<p><strong>Key Points of the Dependency Inversion Principle</strong></p>
<ol>
    <li><strong>High-Level Modules Should Not Depend on Low-Level Modules:</strong> High-level components (which contain the complex logic) should not be tightly coupled with low-level components (which handle the details). Both should interact through interfaces or abstractions.</li>
    <li><strong>Depend on Abstractions, Not on Concrete Implementations:</strong> Code should rely on interfaces or abstract classes instead of concrete classes. This makes it easier to change or swap out implementations without affecting high-level logic.</li>
    <li><strong>Reduces Tight Coupling:</strong> By relying on abstractions, the code becomes less tightly coupled, making it easier to modify, extend, and test.</li>
</ol>

<p><strong>Advantages of the Dependency Inversion Principle</strong></p>
<ol>
    <li><strong>Increased Flexibility:</strong> Since high-level modules can work with any implementation of an abstraction, it's easier to replace or modify parts of the code.</li>
    <li><strong>Improved Testability:</strong> Code that follows DIP is easier to test because you can mock dependencies and isolate components during unit testing.</li>
    <li><strong>Easier Maintenance:</strong> Changes in low-level modules do not impact high-level modules as long as the abstractions remain unchanged, leading to lower maintenance costs.</li>
</ol>

<p><strong>Example of Dependency Inversion Principle in Java</strong></p>

<p>Let’s illustrate the Dependency Inversion Principle with an example involving a notification system.</p>

<p><strong>Without Applying DIP</strong></p>

<p>In this example, we have a <code>NotificationService</code> that directly depends on a concrete class <code>EmailSender</code>.</p>

```java
class EmailSender {
    public void sendEmail(String message) {
        System.out.println("Sending email: " + message);
    }
}

class NotificationService {
    private EmailSender emailSender;

    public NotificationService() {
        emailSender = new EmailSender(); // Direct dependency
    }

    public void sendNotification(String message) {
        emailSender.sendEmail(message);
    }
}
```

<p>In this setup, <code>NotificationService</code> is tightly coupled with <code>EmailSender</code>. If we want to send notifications via SMS or another medium, we would have to modify the <code>NotificationService</code> class.</p>

<p><strong>Applying DIP</strong></p>

<p>To adhere to the Dependency Inversion Principle, we can introduce an interface <code>Notifier</code> that both <code>EmailSender</code> and any other notification type will implement.</p>

<p><strong>1. Define an Abstraction</strong></p>

```java
interface Notifier {
    void send(String message);
}
```

<p><strong>2. Implement the Abstraction</strong></p>

```java
class EmailSender implements Notifier {
    @Override
    public void send(String message) {
        System.out.println("Sending email: " + message);
    }
}

class SMSSender implements Notifier {
    @Override
    public void send(String message) {
        System.out.println("Sending SMS: " + message);
    }
}
```

<p><strong>3. Modify the NotificationService</strong></p>

```java
class NotificationService {
    private Notifier notifier;

    public NotificationService(Notifier notifier) { // Dependency injection
        this.notifier = notifier;
    }

    public void sendNotification(String message) {
        notifier.send(message);
    }
}
```

<p><strong>4. Usage</strong></p>

```java
public class Main {
    public static void main(String[] args) {
        Notifier emailSender = new EmailSender();
        NotificationService notificationService = new NotificationService(emailSender);
        notificationService.sendNotification("Hello via Email!");

        Notifier smsSender = new SMSSender();
        NotificationService smsNotificationService = new NotificationService(smsSender);
        smsNotificationService.sendNotification("Hello via SMS!");
    }
}
```

<p><strong>How This Follows DIP</strong></p>
<ol>
    <li><strong>High-Level Module Dependence:</strong> The <code>NotificationService</code> is no longer directly dependent on <code>EmailSender</code>. Instead, it depends on the <code>Notifier</code> interface. This means that any class that implements <code>Notifier</code> can be used without changing the <code>NotificationService</code>.</li>
    <li><strong>Depend on Abstractions:</strong> By using the <code>Notifier</code> interface, we ensure that the <code>NotificationService</code> is only dependent on abstractions rather than concrete implementations.</li>
    <li><strong>Flexibility:</strong> If we want to add a new notification type (like push notifications), we can simply create a new class implementing <code>Notifier</code> without changing the <code>NotificationService</code>.</li>
    <li><strong>Testability:</strong> During testing, we can easily create mock implementations of <code>Notifier</code> to verify the behavior of <code>NotificationService</code> without relying on concrete implementations.</li>
</ol>

<p>By adhering to the Dependency Inversion Principle, we achieve a more flexible, maintainable, and testable codebase, allowing for easier updates and modifications in the future.</p>


<br>
<br>

<h2>DRY</h2>
<p><strong>DRY Principle</strong> stands for <strong>"Don't Repeat Yourself"</strong> and is all about reducing redundancy in code. When you find yourself writing similar code in multiple places, DRY suggests finding a way to combine it into one reusable piece.</p>

<p><strong>Advantages for Developers:</strong></p>
<ul>
    <li><strong>Less Code to Maintain:</strong> When changes are needed, you only update the code in one place, making maintenance easier and reducing errors.</li>
    <li><strong>Fewer Bugs:</strong> Repeated code often leads to inconsistencies. Using a single, well-tested version reduces bugs and improves reliability.</li>
    <li><strong>Faster Development:</strong> Reusable code blocks save time since developers don't have to rewrite the same functionality repeatedly.</li>
    <li><strong>Cleaner Codebase:</strong> DRY leads to organized and modular code, making it easier for others to understand and contribute.</li>
</ul>

<p><strong>Java Examples:</strong></p>

<ol>
    <li>
        <p><strong>Example 1: Without DRY Principle</strong></p>
        <p>In this example, we calculate the area of a rectangle in multiple parts of the code:</p>

```java
public class RectangleArea {
    public static void main(String[] args) {
        int length1 = 5;
        int width1 = 10;
        int area1 = length1 * width1;
        System.out.println("Area of first rectangle: " + area1);

        int length2 = 7;
        int width2 = 3;
        int area2 = length2 * width2;
        System.out.println("Area of second rectangle: " + area2);
    }
}
```
        <p>This code has redundant calculations and violates the DRY principle.</p>
    </li>
    <li>
        <p><strong>Example 1: Applying DRY Principle</strong></p>
        <p>By creating a reusable method, we can avoid repeating the calculation logic:</p>

```java
public class RectangleArea {
    public static void main(String[] args) {
        System.out.println("Area of first rectangle: " + calculateArea(5, 10));
        System.out.println("Area of second rectangle: " + calculateArea(7, 3));
    }

    // DRY - Reusable method
    public static int calculateArea(int length, int width) {
        return length * width;
    }
}

```
        <p>Now, the <code>calculateArea</code> method is reusable, keeping the code clean and easy to maintain.</p>
    </li>
    <li>
        <p><strong>Example 2: Without DRY Principle</strong></p>
        <p>This example prints user details in multiple places, repeating similar print logic:</p>  

```java
public class UserDetails {
    public static void main(String[] args) {
        String name = "Alice";
        int age = 30;
        String email = "alice@example.com";
        
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Email: " + email);

        // Repeated again
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Email: " + email);
    }
}
```
        <p>This code has redundant print statements and violates the DRY principle.</p>
    </li>
    <li>
        <p><strong>Example 2: Applying DRY Principle</strong></p>
        <p>By creating a reusable method, we can avoid repeating the print logic:</p>

```java
public class UserDetails {
    public static void main(String[] args) {
        String name = "Alice";
        int age = 30;
        String email = "alice@example.com";
        
        // DRY - Print user details through a reusable method
        printUserDetails(name, age, email);
        printUserDetails(name, age, email);
    }

    public static void printUserDetails(String name, int age, String email) {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Email: " + email);
    }
}
```
        <p>Now, the <code>printUserDetails</code> method consolidates the logic, making it easier to update and maintain.</p>
    </li>
</ol>

<br>
<br>

<h2>YAGNI</h2>
<p><strong>The YAGNI principle</strong> stands for "You Aren't Gonna Need It." It’s a principle used in software development that reminds developers to avoid adding features or functionalities until they are actually needed. The idea is that developers should focus only on what’s required now, not on what they <em>might</em> need in the future.</p>

<p>In simple words, <strong>YAGNI advises against writing code based on future possibilities</strong>. Instead, code only what is necessary for the current project requirements. This prevents wasted effort on code that might never be used, making the codebase cleaner and easier to maintain.</p>

<p><strong>Advantages of the YAGNI Principle for Developers</strong></p>

<ol>
  <li><strong>Saves Time and Effort</strong>  
      By focusing only on what’s needed, developers save time and avoid building extra, unused code. This reduces the workload and keeps development focused.
  </li>
  <li><strong>Easier to Maintain</strong>  
      Less code means simpler, more readable codebases. Fewer lines of code make it easier to debug, update, and maintain the application.
  </li>
  <li><strong>Encourages Simplicity</strong>  
      YAGNI keeps the codebase lean. Without unnecessary features, developers create straightforward solutions that are less prone to bugs.
  </li>
  <li><strong>Increases Flexibility</strong>  
      Code evolves as requirements change. Avoiding extra features now makes it easier to adapt the code later without needing to remove or refactor unused portions.
  </li>
</ol>

<p><strong>Examples of YAGNI in Java</strong></p>

<p>Here are some Java examples to illustrate the YAGNI principle in action:</p>

<p><strong>Example 1: Avoiding Unused Methods</strong></p>

<p><strong>Not Following YAGNI</strong>  
Suppose a developer creates a <code>Customer</code> class for an application and decides to add methods like <code>calculateDiscount</code> and <code>generateReport</code> even though they aren’t needed right now:</p>

```java
public class Customer {
    private String name;
    private int age;

    public Customer(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // This method might never be used
    public double calculateDiscount() {
        return 0.0;
    }

    // This method might never be used
    public String generateReport() {
        return "Customer Report";
    }

    // Other necessary methods
}
```

<p><strong>Following YAGNI</strong>  
If these methods aren’t needed immediately, YAGNI suggests omitting them for now:</p>

```java
public class Customer {
    private String name;
    private int age;

    public Customer(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Add methods here only when they are actually needed
}
```

<p><strong>Example 2: Avoiding Premature Optimizations</strong></p>

<p><strong>Not Following YAGNI</strong>  
Let’s say a developer is building a logging feature and anticipates that they <em>might</em> need to log to both a file and a database. They implement code for both options, even though only file logging is needed right now:</p>

```java
public class Logger {
    public void logToFile(String message) {
        // Logic to log to a file
    }

    public void logToDatabase(String message) {
        // Logic to log to a database (not needed now)
    }
}
```

<p><strong>Following YAGNI</strong>  
Instead of writing unnecessary code, the developer would implement only the file logging function until database logging is actually required:</p>

```java
public class Logger {
    public void logToFile(String message) {
        // Logic to log to a file
    }
}
```

<p><strong>Example 3: Avoiding Unnecessary Abstractions</strong></p>

<p><strong>Not Following YAGNI</strong>  
Sometimes developers create interfaces or abstract classes before they’re needed. Here’s an example with an unnecessary interface:</p>

```java
public interface DataProcessor {
    void processData();
}

public class SimpleDataProcessor implements DataProcessor {
    @Override
    public void processData() {
        // Actual processing code
    }
}
```

<p><strong>Following YAGNI</strong>  
If there’s only one way to process data currently, the interface isn’t needed. The developer can add an interface later if other implementations become necessary:</p>

```java
public class DataProcessor {
    public void processData() {
        // Actual processing code
    }
}
```

<p><strong>Conclusion</strong></p>

<p>The YAGNI principle helps developers avoid wasting time and effort by staying focused on what’s necessary right now. By keeping the codebase simple, it’s easier to maintain and extend as new requirements come in.</p>

<br>
<br>

<h2>KISS</h2>
<p><strong>The KISS Principle</strong> stands for "Keep It Simple, Stupid." It’s a concept in software development (and other fields) that encourages simplicity in design and code. The main idea is that <strong>simpler solutions are usually better</strong> because they’re easier to understand, use, and maintain.</p>

<p>In simple words, the KISS principle suggests that <strong>we should avoid making things more complicated than they need to be</strong>. Complex code can be hard to read, fix, and update, while simple code is easier to work with and less likely to have bugs. It doesn’t mean you shouldn’t build advanced features or solve complex problems—just that you should strive to find the simplest way to do it.</p>

<p><strong>Advantages of the KISS Principle for Developers</strong></p>

<ul>
  <li><strong>Easier to Read and Understand</strong>  
      When code is simple, anyone on the team (or even future developers) can quickly understand what it does without needing lots of documentation.
  </li>
  <li><strong>Reduces Bugs and Errors</strong>  
      Simpler code has fewer moving parts, which means there’s less room for errors to slip in. This also makes testing easier.
  </li>
  <li><strong>Speeds Up Development</strong>  
      Keeping things simple allows developers to work faster, reducing time spent on unnecessary complexities.
  </li>
  <li><strong>Makes Maintenance Easier</strong>  
      A straightforward codebase is much easier to update, fix, and extend without breaking other parts of the application.
  </li>
</ul>

<p><strong>Examples of the KISS Principle in Action</strong></p>

<p><strong>Example 1: Using Clear, Simple Code in Java</strong></p>

<p><strong>Not Following KISS</strong>  
A developer might over-complicate a simple function by using fancy syntax or unnecessary conditions:</p>

```java
public boolean isEven(int number) {
    return (number % 2 == 0) ? true : false;
}
```

<p><strong>Following KISS</strong>  
The simpler version is clear and direct, without unnecessary code:</p>

```java
public boolean isEven(int number) {
    return number % 2 == 0;
}
```

<p><strong>Example 2: Avoiding Unnecessary Classes and Methods</strong></p>

<p><strong>Not Following KISS</strong>  
Imagine a developer who creates a separate class and method for a one-line operation:</p>

```java
public class MathUtils {
    public static int doubleNumber(int number) {
        return number * 2;
    }
}
```

<p><strong>Following KISS</strong>  
In this case, just using the multiplication directly when needed is simpler:</p>

<pre><code>int doubled = number * 2;</code></pre>

<p><strong>Example 3: Keeping Functionality Focused and Direct</strong></p>

<p><strong>Not Following KISS</strong>  
A complex, hard-to-follow method that performs multiple actions at once:</p>

```java
public void processOrder(Order order) {
    if (order.isPaid() && order.isInStock() && !order.isShipped()) {
        order.markAsProcessed();
        notifyCustomer(order.getCustomer());
        sendShipment(order);
    }
}
```

<p><strong>Following KISS</strong>  
Breaking it down into smaller, clear methods makes each action easy to understand:</p>

```java
public void processOrder(Order order) {
    if (canProcess(order)) {
        markOrderAsProcessed(order);
        notifyCustomer(order.getCustomer());
        sendShipment(order);
    }
}

private boolean canProcess(Order order) {
    return order.isPaid() && order.isInStock() && !order.isShipped();
}
```

<p><strong>Conclusion</strong></p>

<p>The KISS principle is all about <strong>finding the simplest, most direct way to write code</strong>. By keeping code clear and avoiding unnecessary complexity, developers make software that is easier to understand, debug, and extend.</p>

<br>
<br>

<h2>Separation Of Concerns</h2>
<p><strong>Separation of Concerns (SoC)</strong> is a design principle that suggests <strong>dividing a program into distinct sections</strong>, where each section handles a specific part of the functionality. The main idea is to keep different concerns, or areas of responsibility, separate from each other. This makes code easier to understand, modify, and maintain because each part does only one thing, and changes in one part don’t directly affect the others.</p>

<p>In simple words, <strong>Separation of Concerns means organizing code so each part has its own clear job</strong>. For example, in a web application, the part that handles the user interface should be separate from the part that interacts with the database. This way, if you want to change how the interface looks, you won’t have to worry about breaking the database logic.</p>

<p><strong>Advantages of Separation of Concerns</strong></p>

<ul>
  <li><strong>Easier to Maintain</strong>  
      Code that is divided into clear, separate parts is easier to update and fix without accidentally affecting unrelated areas.
  </li>
  <li><strong>Improves Code Reusability</strong>  
      Components that handle one specific job can often be reused in other projects, making development faster and reducing redundancy.
  </li>
  <li><strong>Simplifies Testing</strong>  
      When each part of the code is responsible for a single task, it’s easier to test each part individually and find errors faster.
  </li>
  <li><strong>Enhances Collaboration</strong>  
      With separate concerns, teams can work on different parts of the code independently, making it easier for multiple developers to collaborate.
  </li>
</ul>

<p><strong>Example of Separation of Concerns in Action</strong></p>

<p>In a basic web application, the concept of SoC is typically divided as follows:</p>

<ul>
  <li><strong>Presentation Layer (View)</strong>  
      This is the part that users interact with directly (e.g., HTML, CSS, and JavaScript). It handles how information is displayed.
  </li>
  <li><strong>Business Logic Layer (Controller)</strong>  
      This part manages the core logic of the application (e.g., calculating, processing, and responding to user actions). It acts as a bridge between the view and the data.
  </li>
  <li><strong>Data Access Layer (Model)</strong>  
      This part deals with the database. It handles tasks like retrieving, updating, and storing data in the database.
  </li>
</ul>

<p><strong>Example Code Using SoC in Java</strong></p>

<p>Imagine a simple app that retrieves and displays user information from a database. Here’s how SoC might look:</p>

<p><strong>Model (Data Layer)</strong>  
This layer defines the structure and logic for interacting with user data:</p>

```java
public class User {
    private int id;
    private String name;

    // Constructor, getters, and setters
}

public class UserRepository {
    public User getUserById(int id) {
        // Logic to fetch user from database
    }
}
```

<p><strong>Controller (Business Logic Layer)</strong>  
This layer handles the main logic and coordinates between the model and view:</p>

```java
public class UserController {
    private UserRepository userRepository;

    public UserController(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public User getUserInfo(int userId) {
        return userRepository.getUserById(userId);
    }
}
```

<p><strong>View (Presentation Layer)</strong>  
This layer deals with displaying data to the user:</p>


```java
public class UserView {
    public void displayUserInfo(User user) {
        System.out.println("User Name: " + user.getName());
    }
}
```

<p><strong>Conclusion</strong></p>

<p>Separation of Concerns helps to create <strong>organized, modular, and easier-to-maintain code</strong>. By dividing responsibilities, SoC ensures that each part of the code has a clear purpose and can be managed, tested, and modified independently.</p>


<br>
<br>

<h2>Modularity</h2>
<p><strong>Modularity</strong> is a principle in software development that involves breaking down a program into smaller, independent parts called <strong>modules</strong>. Each module handles a specific function or task within the application. The idea is to make each module <strong>self-contained</strong> so it can be developed, tested, and used on its own, without needing to know the details of other modules.</p>

<p>In simple words, <strong>modularity means dividing a program into parts that each do one job</strong>. This makes it easier to understand, fix, and update, because you only need to work on the specific part you’re interested in without affecting the whole program.</p>

<p><strong>Advantages of Modularity</strong></p>

<ul>
  <li><strong>Easier to Understand</strong>  
      Smaller, focused modules are easier to read and understand than one big piece of code.
  </li>
  <li><strong>Simplifies Maintenance</strong>  
      If there’s an issue in one module, you can fix or improve it without changing other parts of the program.
  </li>
  <li><strong>Enables Reusability</strong>  
      Modules that handle specific tasks can be reused in different parts of the program or even in other programs.
  </li>
  <li><strong>Supports Collaboration</strong>  
      Different team members can work on different modules at the same time, making development faster and more efficient.
  </li>
</ul>

<p><strong>Example of Modularity</strong></p>

<p>Imagine a program that processes user orders in a shopping application. You might divide it into modules like:</p>

<ul>
  <li><strong>User Module</strong> – Handles user details and authentication.</li>
  <li><strong>Product Module</strong> – Manages product data like names, prices, and stock.</li>
  <li><strong>Order Module</strong> – Processes customer orders and keeps order history.</li>
  <li><strong>Payment Module</strong> – Manages payment processing and verification.</li>
</ul>

<p>Each module has a clear job, making the program organized and easy to work with. If you want to change how payments are processed, you only need to update the <strong>Payment Module</strong> without affecting the other parts of the program.</p>
