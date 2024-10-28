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


