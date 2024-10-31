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

<h2>Creational Patterns</h2>
<p>It deals with creation/instantiation of objects.</p>
<p>In simpler terms, these patterns provide ways to create objects in a way that’s flexible, reusable, and minimizes the complexities in creating those objects directly.</p>
<p><strong>Why Do We Need Creational Patterns?</strong></p>
<p>In software development, we often need to create objects in various ways. But if we do this manually each time, our code can become messy and hard to manage. Creational design patterns help make object creation easier, organized, and adaptable, allowing us to avoid duplicating code and adapt to future changes more easily.</p>
<p>Here are a few main types of creational design patterns:</p>
<ul>
	<li>Singleton Pattern</li>
	<li>Factory Method Pattern</li>
	<li>Abstract Factory Pattern</li>
	<li>Builder Pattern</li>
	<li>Prototype Pattern</li>
</ul>

<br>
<br>
<br>

<h3>Singleton Pattern</h3>
<p>The Singleton Pattern is a design pattern that ensures <strong>a class has only one instance and provides a global point of access to that instance.</strong></p>
<p>This can be useful in scenarios where only one object is needed to coordinate actions across the system, like managing configurations or resources shared by many parts of an application.</p>
<img src="https://refactoring.guru/images/patterns/content/singleton/singleton.png">
<p><strong>Key Points</strong></p>
<ul>
	<li><strong>Single Instance : </strong>It restricts instantiation of the class to just one object.</li>
	<li><strong>Global Access : </strong>The single instance is globally accessible within the application.</li>
	<li><strong>Lazy/Eager Initialization : </strong> Support creating the instance either when needed (lazy) or when the class is loaded (eager).</li>
	<li><strong>Thread Safety : </strong>Implement mechanisms to prevent multiple threads from creating separate instances simultaneously.</li>
	<li><strong>Private Constructor : </strong>Restrict direct instantiation by making the constructor private, forcing the use of the access point</li>
</ul>
<p><strong>How it works ?</strong></p>
<p>Imagine that you created an object, but after a while decided to create a new one. Instead of receiving a fresh object, you’ll get the one you already created.</p>
<p><strong>Initialization Types of Singleton</strong></p>
<p>Singleton class can be instantiated by two methods:</p>
<ul>	
	<li><strong>Early initialization : </strong>In this method, class is initialized whether it is to be used or not. The main advantage of this method is its simplicity. You initiate the class at the time of class loading. Its drawback is that class is always initialized whether it is being used or not.</li>
	<li><strong>Lazy initialization : </strong> In this method, class in initialized only when it is required. It can save you from instantiating the class when you don’t need it. Generally, lazy initialization is used when we create a singleton class.</li>
</ul>
<p><strong>When to use singleton pattern ?</strong></p>
<ul>
	<li><strong>Resource Management :</strong>When you need a single point of access to resources like database connections or file systems.</li>
	<li><strong>Configuration Management :</strong>For managing application-wide configurations, settings, or logging where multiple instances could lead to inconsistencies.</li>
	<li><strong>Caching :</strong> For data caching, where multiple copies of cache data would be redundant and resource-consuming.</li>
</ul>
<p><strong>Advantages of Singleton Pattern</strong></p>
<ul>
	<li><strong>Controlled Access to a Single Instance : </strong>Provides controlled access to shared resources.</li>
	<li><strong>Reduced Memory Usage : </strong> Only one instance is created that too lazy, which can save memory</li>
	<li><strong>Consistency : </strong>Maintains data consistency by ensuring only one instance modifies a resource or setting.</li>
</ul>
<p><strong>How to implement</strong></p>
<ol>
	<li>Add a private static field to the class for storing the singleton instance.</li>
	<li>Declare a public static creation method for getting the singleton instance.</li>
	<li>Implement “lazy initialization” inside the static method. It should create a new object on its first call and put it into the static field. The method should always return that instance on all subsequent calls.</li>
	<li>Make the constructor of the class private. The static method of the class will still be able to call the constructor, but not the other objects.</li>
	<li>Go over the client code and replace all direct calls to the singleton’s constructor with calls to its static creation method.</li>
</ol>
<p><strong>Examples of Singleton Pattern in Python and Java</strong></p>

```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {}  // Private constructor prevents instantiation from outside

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}

class Main {
    public static void main(String[] args)
    {
        // Testing Singleton behavior
		Singleton obj1 = Singleton.getInstance();
		Singleton obj2 = Singleton.getInstance();
		System.out.println(obj1 == obj2);  // Output: true, both are the same instance
    }
}

```

```python
class Singleton:
    __instance=None

    @staticmethod
    def getInstance():
        if(Singleton.__instance==None):
            Singleton.__instance=Singleton()
        return Singleton.__instance

    def __new__(cls):
        if(cls.__instance==None):
            cls.__instance=super(Singleton,cls).__new__(cls);
        return cls.__instance

obj1=Singleton.getInstance()
obj2=Singleton.getInstance()
print(obj1==obj2) // Output: true, both are the same instance
```

<p>Singleton obj is not created until we need it and call the getInstance() method. This is called lazy instantiation. The main problem with the above method is that it is not thread-safe. Consider the following execution sequence.</p>
<p>If two threads calls the getInstance Method at same time in different threads, it will create two different objects.</p>
<p>To address this issue we can use synchronized block or eager initialization as follows</p>

<p><strong>Thread Safe</strong></p>

```java
// Thread Synchronized Java implementation of
// singleton design pattern
class Singleton {
    private static Singleton obj;
    private Singleton() {}

    // Only one thread can execute this at a time
    public static synchronized Singleton getInstance()
    {
        if (obj == null)
            obj = new Singleton();
        return obj;
    }
}
```

<p>Here using synchronized makes sure that only one thread at a time can execute getInstance(). The main disadvantage of this method is that using synchronized every time while creating the singleton object is expensive and may decrease the performance of your program. However, if the performance of getInstance() is not critical for your application this method provides a clean and simple solution.</p>
<p>For python,</p>


<p><strong>Eager Instantiation</strong></p>

```java
// Static Eager initializer based Java implementation of
// singleton design pattern
class Singleton {
    private static Singleton obj = new Singleton();
    private Singleton() {}

    public static Singleton getInstance() { return obj; }
}
```

```python
# Static Eager initializer based Java implementation of
# singleton design pattern
class Singleton:
    __instance=None

    @staticmethod
    def getInstance():
        if(Singleton.__instance==None):
            Singleton.__instance=Singleton()
        return Singleton.__instance

    def __new__(cls):
        if(cls.__instance==None):
            cls.__instance=super(Singleton,cls).__new__(cls);
        return cls.__instance

# Immediately instantiating the singleton
obj1=Singleton.getInstance()
```
<p>Here we have created an instance of a singleton in a static initializer. JVM executes a static initializer when the class is loaded and hence this is guaranteed to be thread-safe. Use this method only when your singleton class is light and is used throughout the execution of your program.</p>
<p>In Python, eager instantiation can be implemented by creating the instance as soon as the class is defined. Here’s how it works:</p>

<p><strong>Double Checked Locking</strong></p>
<p>If you notice carefully once an object is created synchronization is no longer useful because now obj will not be null and any sequence of operations will lead to consistent results. So we will only acquire the lock on the getInstance() once when the obj is null. This way we only synchronize the first way through, just what we want. </p>

```java
// Double Checked Locking based Java implementation of
// singleton design pattern
class Singleton {
    private static volatile Singleton obj = null;
    private Singleton() {}

    public static Singleton getInstance()
    {
        if (obj == null) {
            // To make thread safe
            synchronized (Singleton.class)
            {
                // check again as multiple threads
                // can reach above step
                if (obj == null)
                    obj = new Singleton();
            }
        }
        return obj;
    }
}

```

<p>It is easy to notice that once an object is created, the synchronization of the threading is no longer useful because now the object will never be equal to None and any sequence of operations will lead to consistent results. </p>


```python
import threading

class SynchronizedSingleton:
    _instance = None
    _lock = threading.Lock()  # Create a lock object

    def __new__(cls):
        # Acquiring the lock to ensure only one thread creates the instance
        with cls._lock:
            if cls._instance is None:
                cls._instance = super(SynchronizedSingleton, cls).__new__(cls)
        return cls._instance

    @staticmethod
    def getInstance():
        if(Singleton._instance==None):
            Singleton._instance=Singleton()
        return Singleton._instance

    def some_method(self):
        # Ensuring thread safety within a method
        with self._lock:
            # Critical section where only one thread can execute at a time
            print("Executing some method safely in a thread-safe way")

# Testing Synchronized Singleton
singleton1 = SynchronizedSingleton()
singleton2 = SynchronizedSingleton()
print(singleton1 == singleton2)  # Output: True

# Creating threads to test thread safety
def access_singleton():
    singleton = SynchronizedSingleton()
    singleton.some_method()

threads = [threading.Thread(target=access_singleton) for _ in range(5)]
for thread in threads:
    thread.start()
for thread in threads:
    thread.join()
```

<ul>	
	<li>Lock Creation: The _lock is a class attribute, ensuring it is shared among all instances of the class.</li>
	<li>Thread-safe Singleton Creation: In __new__, the lock is acquired before creating the singleton instance, ensuring only one thread can create it.</li>
	<li>Thread-safe Method: The some_method uses the same lock, ensuring thread safety for that method specifically.</li>
</ul>



<br>
<br>
<br>


<h3>Factory Design Pattern</h3>
<p>The factory design pattern is used when we have a superclass with multiple sub-classes and based on input, we need to return one of the sub-class. This pattern takes out the responsibility of the instantiation of that sub-class from the client program to the factory class.</p>

<p><strong>Key Points of the Factory Pattern</strong></p>
<ul>
	<li><strong>Encapsulation of Object Creation : </strong>It hides the logic of object creation, simplifying client code. It Creates objects without exposing the instantiation logic to the client.</li>
	<li><strong>Flexibility : </strong>New types of objects can be added with minimal changes to client code, because it is taken care by factory class</li>
	<li><strong>Single Responsibility Principle : </strong>The factory handles the creation, so the main code can focus on other tasks.So, each class is reposnisble for its main theme only.</li>
</ul>

<p><strong>How the Factory Pattern Works</strong></p>
<p>The Factory Pattern uses a "Factory" class or method to create and return instances of objects. This factory class can contain a method, often called create or get_instance, that decides and returns an instance based on inputs or conditions.</p>
<p>So, then client code can ask to create object based on its need.</p>
<p>this reduces code complexity in client side</p>

<p><strong>When to Use the Factory Pattern</strong></p>
<ul>
	<li>When the exact type of object to be created is not known until runtime.</li>
	<li>When creating objects involves complex logic or additional configuration.</li>
	<li>When working with a family of related classes where the client should not need to know about each specific class.</li>
</ul>

<p><strong>Advantages of the Factory Pattern</strong></p>
<ul>
	<li><strong>Reduced Code Duplication : </strong>Centralizes object creation code in the factory.</li>
	<li><strong>Improved Maintenance : </strong>Changes in object creation logic affect only the factory.</li>
	<li><strong>Scalability : </strong>Adding new types is easier since only the factory method requires updating.</li>
</ul>

<p><strong>Disadvantages</strong></p>
<ul>
	<li>Each factory has to be initialized before using it.</li>
	<li>More difficult to implement.</li>
</ul>

<p><strong>Applications</strong></p>
<ul>
	<li>GUI Components: Creating UI components like buttons, text boxes, etc., based on operating systems.</li>
	<li>Database Connections: Returning specific database connections based on configuration.</li>
	<li>Logging Systems: Creating loggers for different types of logging (file, console, network).</li>
</ul>

<p><strong>Examples</strong></p>

<p><strong>Factory Design Pattern Super Class</strong></p>
<p>Super class in factory design pattern can be an interface, abstract class or a normal java class. For our factory design pattern example, we have abstract super class with overridden toString() method for testing purpose.</p>

```java
package com.journaldev.design.model;

public abstract class Computer {
	
	public abstract String getRAM();
	public abstract String getHDD();
	public abstract String getCPU();
	
	@Override
	public String toString(){
		return "RAM= "+this.getRAM()+", HDD="+this.getHDD()+", CPU="+this.getCPU();
	}
}
```
<p><strong>Factory Design Pattern Sub Classes</strong></p>
<p>Let’s say we have two sub-classes PC and Server with below implementation.</p>

```java
package com.journaldev.design.model;

public class PC extends Computer {

	private String ram;
	private String hdd;
	private String cpu;
	
	public PC(String ram, String hdd, String cpu){
		this.ram=ram;
		this.hdd=hdd;
		this.cpu=cpu;
	}
	@Override
	public String getRAM() {
		return this.ram;
	}

	@Override
	public String getHDD() {
		return this.hdd;
	}

	@Override
	public String getCPU() {
		return this.cpu;
	}

}


package com.journaldev.design.model;

public class Server extends Computer {

	private String ram;
	private String hdd;
	private String cpu;
	
	public Server(String ram, String hdd, String cpu){
		this.ram=ram;
		this.hdd=hdd;
		this.cpu=cpu;
	}
	@Override
	public String getRAM() {
		return this.ram;
	}

	@Override
	public String getHDD() {
		return this.hdd;
	}

	@Override
	public String getCPU() {
		return this.cpu;
	}

}
```

<p>Notice that both the classes are extending Computer super class.</p>

<p><strong>Factory Class</strong></p>
<p>Now that we have super classes and sub-classes ready, we can write our factory class. Here is the basic implementation.</p>

```java
package com.journaldev.design.factory;

import com.journaldev.design.model.Computer;
import com.journaldev.design.model.PC;
import com.journaldev.design.model.Server;

public class ComputerFactory {

	public static Computer getComputer(String type, String ram, String hdd, String cpu){
		if("PC".equalsIgnoreCase(type)) return new PC(ram, hdd, cpu);
		else if("Server".equalsIgnoreCase(type)) return new Server(ram, hdd, cpu);
		
		return null;
	}
}
```

<p>Here is a simple test client program that uses above factory design pattern implementation.</p>

```java
package com.journaldev.design.test;

import com.journaldev.design.factory.ComputerFactory;
import com.journaldev.design.model.Computer;

public class TestFactory {

	public static void main(String[] args) {
		Computer pc = ComputerFactory.getComputer("pc","2 GB","500 GB","2.4 GHz");
		Computer server = ComputerFactory.getComputer("server","16 GB","1 TB","2.9 GHz");
		System.out.println("Factory PC Config::"+pc);
		System.out.println("Factory Server Config::"+server);
	}

}

// Output
// Factory PC Config::RAM= 2 GB, HDD=500 GB, CPU=2.4 GHz
// Factory Server Config::RAM= 16 GB, HDD=1 TB, CPU=2.9 GHz
```

```python
from abc import ABC,abstractmethod

class Computer(ABC):

    @abstractmethod
    def getRam(self):
        pass

    @abstractmethod
    def getStorage(self):
        pass

    @abstractmethod
    def getCPU(self):
        pass

    def __str__(self):
        return "RAM : {} GB - Storage : {} GB - CPU : {} Cores".format(self.getRam(),self.getStorage(),self.getCPU())

class PC(Computer):

    def __init__(self,ram,storage,cpu):
        self.ram=ram
        self.storage=storage
        self.cpu=cpu

    def getRam(self):
        return self.ram

    def getStorage(self):
        return self.storage

    def getCPU(self):
        return self.cpu

class Server(Computer):

    def __init__(self,ram,storage,cpu):
        self.ram=ram
        self.storage=storage
        self.cpu=cpu

    def getRam(self):
        return self.ram

    def getStorage(self):
        return self.storage

    def getCPU(self):
        return self.cpu


class ComputerFactory:

    @staticmethod
    def getComputer(type,ram,storage,cpu):
        if(type=="PC"):
            return PC(ram,storage,cpu)
        if(type=="Server"):
            return Server(ram,storage,cpu)

class Client:

    def main(self):
        pc=ComputerFactory.getComputer("PC",12,512,10);
        server=ComputerFactory.getComputer("PC",12,512,10);
        print("PC :",pc)
        print("Server :",server)


client=Client()
client.main()

```

<p><strong>Some important points about Factory Design Pattern method are;</strong></p>
<ul>
	<li>We can keep Factory class Singleton or we can keep the method that returns the subclass as static.</li>
	<li>Notice that based on the input parameter, different subclass is created and returned. getComputer is the factory method.</li>
</ul>

<img src="https://journaldev.nyc3.cdn.digitaloceanspaces.com/2013/05/factory-pattern-java.png">

<p><strong>Example-2 : </strong></p>
<img src="https://images.javatpoint.com/images/designpattern/factorymethod.jpg">

<p><strong>Example-3 : </strong></p>
<img src="https://www.tutorialspoint.com/design_pattern/images/factory_pattern_uml_diagram.jpg">

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def draw(self):
        pass
class Circle(Shape):
    def draw(self):
        print("Drawing a Circle")

class Square(Shape):
    def draw(self):
        print("Drawing a Square")

class Rectangle(Shape):
    def draw(self):
        print("Drawing a Rectangle")
class ShapeFactory:
    @staticmethod
    def create_shape(shape_type):
        if shape_type == "circle":
            return Circle()
        elif shape_type == "square":
            return Square()
        elif shape_type == "rectangle":
            return Rectangle()
        else:
            raise ValueError(f"Unknown shape type: {shape_type}")
# Client code
shape_type = "circle"  # This could come from user input, config, etc.
shape = ShapeFactory.create_shape(shape_type)
shape.draw()  # Output: "Drawing a Circle"

```

<p>The Factory Pattern is widely used in situations where object creation varies based on conditions and simplifies code maintenance by centralizing object creation logic.</p>

<p><strong>Real-Time Analogy for the Factory Pattern</strong></p>
<p>Imagine a <strong>bakery</strong> where you can order different types of cakes, like chocolate, vanilla, or strawberry. When a customer places an order, they don’t need to know the exact recipe or ingredients to bake each type of cake. They just specify the cake type they want, and the bakery staff (acting as the "factory") decides how to make it, picking the correct ingredients and process based on the type.</p>
<p>Similarly, in programming, the Factory Pattern lets a client code specify the type of object it needs (like a "chocolate cake" or "vanilla cake" in our analogy) without knowing the specific details of how that object is created. This abstraction makes it easier to maintain and expand, as new cake types can be added to the bakery without affecting the customers' orders.</p>

<p><strong>Real-Time Applications of the Factory Pattern</strong></p>
<ol>
    <li><strong>Database Connection Managers</strong>: Many applications need to connect to different databases (like MySQL, PostgreSQL, Oracle) based on configuration settings. Using a factory pattern, a <strong>DatabaseFactory</strong> can create connections based on the database type provided in the configuration, without client code needing to handle the specifics of each database connection.</li>
    <li><strong>Logging Frameworks</strong>: Logging systems often support different log types (console, file, network). A <strong>LoggerFactory</strong> can be used to create appropriate logger instances based on configuration, so a system can log messages in various formats without modifying the core logging code.</li>
    <li><strong>Payment Gateways in E-commerce</strong>: When processing payments, an e-commerce application might support multiple payment providers (like PayPal, Stripe, or Square). A <strong>PaymentFactory</strong> can handle the logic of selecting and returning the appropriate payment gateway instance based on the payment method chosen by the customer.</li>
    <li><strong>Document Processing in Office Applications</strong>: Applications that handle multiple file formats (like PDFs, Word documents, and spreadsheets) can use a factory to create the correct document type. For example, if a user opens a PDF, a <strong>DocumentFactory</strong> can create a <strong>PDFDocument</strong> object, while for a Word file, it can create a <strong>WordDocument</strong> object.</li>
    <li><strong>Notification Systems</strong>: In systems that send notifications through multiple channels (email, SMS, push notifications), a <strong>NotificationFactory</strong> can create instances of each notification type based on the user's preferences or the app's requirements.</li>
</ol>
<p>The Factory Pattern helps manage complexity in such systems by encapsulating object creation, allowing easy addition or modification of supported types without changing the core logic.</p>

<br>
<br>
<br>

<h3>Abstract Factory Design Pattern</h3>
<p><strong>Factory Pattern:</strong></p>
<ul>
    <li>Involves <strong>one superclass</strong> and its <strong>subclasses</strong>.</li>
    <li>The <strong>factory class</strong> is responsible for creating an object based on a single superclass (or interface) and produces one of its subclasses based on client requests.</li>
    <li>Typically, it’s used when there’s a single type of product but with different variations or implementations (subclasses) that a client might request.</li>
</ul>

<p><strong>Abstract Factory Pattern:</strong></p>
<ul>
    <li>Can involve <strong>multiple superclasses</strong> (or interfaces) and their <strong>respective subclasses</strong>.</li>
    <li>The <strong>abstract factory</strong> organizes and groups similar object families and creates them based on client requests.</li>
    <li>It can also group objects of same superclass</li>
    <li>Used when there are families of related products, and the client wants to ensure consistent creation of related object groups. For example, in a GUI framework, an abstract factory might ensure all components (buttons, checkboxes) match the theme (dark or light).</li>
</ul>

<p>The <strong>Abstract Factory Pattern</strong> is a design pattern that provides an interface for creating families of related objects without specifying their exact classes. It allows a client to create sets of related products that work well together, ensuring consistency and flexibility in how these products are created and used.</p>

<p>Abstract Factory pattern is almost similar to Factory Pattern and is considered as another layer of abstraction over factory pattern. Abstract Factory patterns work around a super-factory which creates other factories.</p>
<p>This factory is also called as factory of factories</p>
<p>In Abstract Factory pattern an interface is responsible for creating a factory of related objects without explicitly specifying their classes. Each generated factory can give the objects as per the Factory pattern.</p>

<p><strong>Key Points of the Abstract Factory Pattern</strong></p>
<ul>
    <li><strong>Family of Objects</strong>: It’s used to create groups (families) of related or dependent objects.</li>
    <li><strong>Encapsulation</strong>: It encapsulates the details of object creation in separate factories.</li>
    <li><strong>Interface Flexibility</strong>: It defines an interface that lets client code interact with products through abstract interfaces, allowing flexibility and easy modification.</li>
</ul>

<p><strong>How the Abstract Factory Pattern Works</strong></p>
<p>The Abstract Factory Pattern uses:</p>
<ul>
    <li>An <strong>abstract factory</strong> This is the main interface that declares a set of creation methods for creating the abstract products. It serves as a contract for concrete factories to implement. The abstract factory typically represents a family of related products.</li>
    <li><strong>Concrete factory classes</strong> These are the implementations of the abstract factory interface. Each concrete factory is responsible for creating a specific set of products, which are compatible within a specific variation or family.</li>
    <li><strong>Abstract products</strong> This represents the interface of the products that the abstract factory creates. It defines a set of operations that concrete products must implement.</li>
    <li><strong>Concrete products</strong> These are the actual product implementations created by concrete factories. Each concrete factory creates a different variant of the product by implementing the abstract product interface.</li>
</ul>

<p><strong>When to Use the Abstract Factory Pattern</strong></p>
<ol>
    <li>When a system needs to be independent of how its objects are created.</li>
    <li>When a system needs to work with multiple families of related products.</li>
    <li>When product families require consistent usage: For instance, using a specific GUI style across an application.</li>
</ol>

<p><strong>Advantages of the Abstract Factory Pattern</strong></p>
<ol>
    <li><strong>Increased Flexibility</strong>: Changing a product family requires changing only the factory.</li>
    <li><strong>Code Consistency</strong>: Ensures that related products are used together by creating them through the same factory.</li>
    <li><strong>Easy Scalability</strong>: Adding new families or products becomes simpler.</li>
</ol>

<p><strong>Example of Abstract Factory Pattern (Multiple Superclasses) in Python</strong></p>

<p>Here we have two superclasses <strong>Button</strong> and <strong>Checkbox</strong>, and each has subclasses associated with it: <strong>DarkButton</strong>, <strong>LightButton</strong>, <strong>DarkCheckbox</strong>, and <strong>LightCheckbox</strong>.</p>
<p>When a client requests <strong>DarkUI</strong>, it should return <strong>DarkCheckbox</strong> and <strong>DarkButton</strong> together.</p>
<p>When a client requests <strong>LightUI</strong>, it should return <strong>LightCheckbox</strong> and <strong>LightButton</strong> together.</p>
<p>Since we need to deal with a group of related objects, we can use the Abstract Factory Pattern.</p>
<ul>
    <li><strong>Abstract Products:</strong> Button, Checkbox</li>
    <li><strong>Concrete Products:</strong> DarkButton, LightButton, DarkCheckbox, LightCheckbox</li>
    <li><strong>Abstract Factory:</strong> GUIFactory</li>
    <li><strong>Concrete Factories:</strong> DarkFactory, LightFactory</li>
</ul>

<p><strong>Step 1: Define Abstract Product Interfaces</strong></p>

```python
from abc import ABC, abstractmethod

# Abstract product interfaces
class Button(ABC):
    @abstractmethod
    def render(self):
        pass

class Checkbox(ABC):
    @abstractmethod
    def check(self):
        pass
```

<p><strong>Step 2: Implement Concrete Products</strong></p>

```python
# Dark theme products
class DarkButton(Button):
    def render(self):
        print("Rendering a dark button")

class DarkCheckbox(Checkbox):
    def check(self):
        print("Checking a dark checkbox")

# Light theme products
class LightButton(Button):
    def render(self):
        print("Rendering a light button")

class LightCheckbox(Checkbox):
    def check(self):
        print("Checking a light checkbox")
```

<p><strong>Step 3: Define Abstract Factory Interface</strong></p>

```python
class GUIFactory(ABC):
    @abstractmethod
    def create_button(self):
        pass

    @abstractmethod
    def create_checkbox(self):
        pass
```

<p><strong>Step 4: Implement Concrete Factories</strong></p>

```python
# Factory for creating dark theme components
class DarkFactory(GUIFactory):
    def create_button(self):
        return DarkButton()

    def create_checkbox(self):
        return DarkCheckbox()

# Factory for creating light theme components
class LightFactory(GUIFactory):
    def create_button(self):
        return LightButton()

    def create_checkbox(self):
        return LightCheckbox()
```

<p><strong>Step 5: Client Code</strong></p>

```python
# Client code, which uses the factory without knowing specific product details
def create_ui(factory: GUIFactory):
    button = factory.create_button()
    checkbox = factory.create_checkbox()
    button.render()
    checkbox.check()

# Using the Dark theme
dark_factory = DarkFactory()
create_ui(dark_factory)

# Using the Light theme
light_factory = LightFactory()
create_ui(light_factory)
```

<p><strong>Applications of Abstract Factory Pattern</strong></p>
<ul>
    <li><strong>GUI Toolkits</strong>: For creating cross-platform UIs where different OSs have different widgets.</li>
    <li><strong>Database Access Systems</strong>: For supporting multiple databases like SQL and NoSQL, with different query components.</li>
    <li><strong>Operating System Compatibility</strong>: Creating OS-specific configurations or system calls.</li>
</ul>

<p>The Abstract Factory Pattern enables developers to create families of related objects while ensuring consistency and flexibility, making it ideal for scalable, platform-agnostic applications.</p>

<p><strong>Real-Time Analogy for the Abstract Factory Pattern</strong></p>
<p><strong>Example of Abstract Factory Pattern for Car Manufacturing Plant in Python</strong></p>

<p>Imagine a <strong>car manufacturing plant</strong> that builds cars based on customer preferences for different configurations, such as <strong>Economy</strong>, <strong>Luxury</strong>, and <strong>Sports</strong>. Each configuration requires specific parts, like different engines, interiors, and tires. The customer simply chooses the type of car they want, and the factory produces all the necessary parts and assembles them without the customer needing to know the details.</p>

<p>In this example, the <strong>Abstract Factory Pattern</strong> is used to create <strong>families of related objects</strong> based on the selected car configuration.</p>

<ul>
    <li><strong>Abstract Products:</strong> Engine, Interior, Tires</li>
    <li><strong>Concrete Products:</strong> EconomyEngine, LuxuryEngine, SportsEngine, EconomyInterior, LuxuryInterior, SportsInterior, EconomyTires, LuxuryTires, SportsTires</li>
    <li><strong>Abstract Factory:</strong> CarFactory</li>
    <li><strong>Concrete Factories:</strong> EconomyFactory, LuxuryFactory, SportsFactory</li>
</ul>

<p><strong>Step 1: Define Abstract Product Interfaces</strong></p>

```python
from abc import ABC, abstractmethod

# Abstract product interfaces
class Engine(ABC):
    @abstractmethod
    def create(self):
        pass

class Interior(ABC):
    @abstractmethod
    def design(self):
        pass

class Tires(ABC):
    @abstractmethod
    def make(self):
        pass
```

<p><strong>Step 2: Implement Concrete Products</strong></p>

```python
# Economy car parts
class EconomyEngine(Engine):
    def create(self):
        print("Creating economy engine")

class EconomyInterior(Interior):
    def design(self):
        print("Designing economy interior")

class EconomyTires(Tires):
    def make(self):
        print("Making economy tires")

# Luxury car parts
class LuxuryEngine(Engine):
    def create(self):
        print("Creating luxury engine")

class LuxuryInterior(Interior):
    def design(self):
        print("Designing luxury interior")

class LuxuryTires(Tires):
    def make(self):
        print("Making luxury tires")

# Sports car parts
class SportsEngine(Engine):
    def create(self):
        print("Creating sports engine")

class SportsInterior(Interior):
    def design(self):
        print("Designing sports interior")

class SportsTires(Tires):
    def make(self):
        print("Making sports tires")

```

<p><strong>Step 3: Define Abstract Factory Interface</strong></p>

```python
class CarFactory(ABC):
    @abstractmethod
    def create_engine(self):
        pass

    @abstractmethod
    def create_interior(self):
        pass

    @abstractmethod
    def create_tires(self):
        pass
```

<p><strong>Step 4: Implement Concrete Factories</strong></p>

```python
# Factory for creating economy car parts
class EconomyFactory(CarFactory):
    def create_engine(self):
        return EconomyEngine()

    def create_interior(self):
        return EconomyInterior()

    def create_tires(self):
        return EconomyTires()

# Factory for creating luxury car parts
class LuxuryFactory(CarFactory):
    def create_engine(self):
        return LuxuryEngine()

    def create_interior(self):
        return LuxuryInterior()

    def create_tires(self):
        return LuxuryTires()

# Factory for creating sports car parts
class SportsFactory(CarFactory):
    def create_engine(self):
        return SportsEngine()

    def create_interior(self):
        return SportsInterior()

    def create_tires(self):
        return SportsTires()
```

<p><strong>Step 5: Client Code</strong></p>

```python
# Client code, which uses the factory without knowing specific product details
def build_car(factory: CarFactory):
    engine = factory.create_engine()
    interior = factory.create_interior()
    tires = factory.create_tires()
    
    engine.create()
    interior.design()
    tires.make()

# Building an economy car
economy_factory = EconomyFactory()
print("Building Economy Car:")
build_car(economy_factory)

# Building a luxury car
luxury_factory = LuxuryFactory()
print("\nBuilding Luxury Car:")
build_car(luxury_factory)

# Building a sports car
sports_factory = SportsFactory()
print("\nBuilding Sports Car:")
build_car(sports_factory)

```

<p>In this example, the <strong>CarFactory</strong> is an abstract factory that creates a family of related parts for each car type (Engine, Interior, Tires) using specific factories. The <strong>EconomyFactory</strong>, <strong>LuxuryFactory</strong>, and <strong>SportsFactory</strong> each provide the appropriate parts for their respective car configurations, so the client can easily build any car type without needing to know about individual parts.</p>


<p>Similarly, the Abstract Factory Pattern allows a client (like the customer) to create families of related objects (car parts) through an abstract factory. The details of object creation are managed by the factory, allowing for different families of related objects to be produced as required.</p>

<p><strong>Real-Time Applications of the Abstract Factory Pattern</strong></p>
<ol>
    <li><strong>Cross-Platform UI Libraries</strong>: Many applications need to run on different operating systems (Windows, macOS, Linux) with distinct UI elements. An abstract factory can create platform-specific UI elements while ensuring a consistent look and feel across the application.</li>
    <li><strong>Web Browser Rendering Engines</strong>: Modern web browsers support different rendering engines for handling various content types (e.g., text, images, video). An abstract factory can generate rendering objects for each type, depending on the content being displayed, allowing flexible and efficient content rendering.</li>
    <li><strong>Game Development</strong>: Games often have different themes (e.g., fantasy, sci-fi, horror). The Abstract Factory Pattern can create themed elements like characters, weapons, and backgrounds by grouping related object families based on the game theme.</li>
    <li><strong>Device Drivers</strong>: Many systems need drivers for different hardware configurations. Using the Abstract Factory Pattern, a system can generate drivers for different hardware families, like graphics cards or sound systems, based on the machine's specific hardware requirements.</li>
    <li><strong>Cloud Storage and Database Services</strong>: Cloud platforms often need to support multiple storage or database systems (e.g., SQL, NoSQL, object storage). An abstract factory can be used to create and manage connections for each storage type, allowing applications to interact with various storage solutions seamlessly.</li>
</ol>
<p>The Abstract Factory Pattern enables easy customization for various configurations and scalable solutions in applications where consistency across families of objects is essential.</p>


<br>
<br>
<br>


<h3>Builder Design Pattern</h3>

<p>The Builder Design Pattern was introduced to address some limitations of the Factory and Abstract Factory patterns, especially when creating objects with many attributes. Here’s how the Builder pattern solves these issues:</p>
<ul>
    <li><strong>Too Many Arguments in Factory Patterns:</strong></li>
    <ul>
        <li>When using Factory or Abstract Factory patterns, passing a large number of arguments from the client program to the factory can lead to errors, particularly when arguments are of similar types. It can be challenging to ensure the correct order and maintain readability.</li>
    </ul>
    <li><strong>Optional Parameters Issue:</strong></li>
    <ul>
        <li>In Factory patterns, we must provide values for all parameters, including optional ones. This often forces us to pass NULL or default values for these optional attributes, which complicates the code and adds unnecessary detail.</li>
    </ul>
    <li><strong>Complex Object Creation in Factory Classes:</strong></li>
    <ul>
        <li>If the object is complex and has a lot of construction logic, placing all that logic inside Factory classes can make the code confusing. It can blur the responsibilities of classes, making Factory classes hard to maintain and extend.
        </li>
    </ul>
    <p>The Builder Pattern provides a cleaner, more organized way to construct objects by separating the object creation logic into manageable steps, handling optional attributes effectively, and improving readability and maintainability.</p>
</ul>

<p><strong>Builder Design Pattern</strong> helps you construct complex objects step-by-step. Rather than having a constructor with lots of parameters (which can get confusing), the Builder pattern uses a builder object to guide the construction of an object.</p>

<p><strong>Simple Explanation</strong></p>
<p>In simple terms, the Builder pattern lets you create an object piece by piece by specifying only the parts you want, without knowing every detail. Think of it like ordering a custom pizza where you add one topping at a time.</p>

<p><strong>Advantages for Developers</strong></p>
<ul>
  <li><strong>Increased Flexibility</strong>: The Builder pattern provides more control over the object creation process. It lets you assemble objects with different configurations, which is useful if you need to create objects with varied details.</li>
  <li><strong>Improved Readability</strong>: Instead of a complicated constructor with many parameters, you can add each part of an object gradually, making the code more readable and easier to understand.</li>
  <li><strong>Encapsulated Construction Logic</strong>: Complex construction logic is separated into the builder class, making the main class simpler.</li>
</ul>

<p><strong>When to Use the Builder Pattern</strong></p>
<ul>
  <li>When you want to create a complex object step-by-step.</li>
  <li>When a class has multiple parameters and optional values that could make constructors long and confusing.</li>
  <li>When you need to enforce consistency while constructing objects with variations.</li>
</ul>

<p><strong>Real-Time Analogy</strong></p>
<p>Think of building a house. You may want different configurations for your house: the number of rooms, floors, types of windows, and so on. A builder (construction manager) allows you to specify each detail one step at a time rather than needing every detail from the start. The builder helps you configure each piece gradually until the house is complete.</p>

<p><strong>Real-Time Applications</strong></p>
<ul>
  <li><strong>Document Creation Tools</strong>: Creating documents with various components, like headings, footers, tables, etc., where each part can be customized.</li>
  <li><strong>Graphical User Interface (GUI) Tools</strong>: Building complex UIs with configurable elements such as buttons, text boxes, and drop-downs.</li>
  <li><strong>Car Manufacturing</strong>: Configuring different models with various parts like engine type, transmission, paint color, etc.</li>
</ul>

<p><strong>Python Examples</strong></p>

<p><strong>Basic Builder Pattern Example</strong></p>

```java
package com.journaldev.design.builder;

public class Computer {
    
    //required parameters
    private String HDD;
    private String RAM;
    
    //optional parameters
    private boolean isGraphicsCardEnabled;
    private boolean isBluetoothEnabled;
    

    public String getHDD() {
        return HDD;
    }

    public String getRAM() {
        return RAM;
    }

    public boolean isGraphicsCardEnabled() {
        return isGraphicsCardEnabled;
    }

    public boolean isBluetoothEnabled() {
        return isBluetoothEnabled;
    }
    
    private Computer(ComputerBuilder builder) {
        this.HDD=builder.HDD;
        this.RAM=builder.RAM;
        this.isGraphicsCardEnabled=builder.isGraphicsCardEnabled;
        this.isBluetoothEnabled=builder.isBluetoothEnabled;
    }
    
    //Builder Class
    public static class ComputerBuilder{

        // required parameters
        private String HDD;
        private String RAM;

        // optional parameters
        private boolean isGraphicsCardEnabled;
        private boolean isBluetoothEnabled;
        
        public ComputerBuilder(String hdd, String ram){
            this.HDD=hdd;
            this.RAM=ram;
        }

        public ComputerBuilder setGraphicsCardEnabled(boolean isGraphicsCardEnabled) {
            this.isGraphicsCardEnabled = isGraphicsCardEnabled;
            return this;
        }

        public ComputerBuilder setBluetoothEnabled(boolean isBluetoothEnabled) {
            this.isBluetoothEnabled = isBluetoothEnabled;
            return this;
        }
        
        public Computer build(){
            return new Computer(this);
        }

    }

}
```
<p>Notice that Computer class has only getter methods and no public constructor. So the only way to get a Computer object is through the ComputerBuilder class. Here is a builder pattern example test program showing how to use Builder class to get the object.</p>

```java
package com.journaldev.design.test;

import com.journaldev.design.builder.Computer;

public class TestBuilderPattern {

    public static void main(String[] args) {
        //Using builder to get the object in a single line of code and 
                //without any inconsistent state or arguments management issues     
        Computer comp = new Computer.ComputerBuilder(
                "500 GB", "2 GB").setBluetoothEnabled(true)
                .setGraphicsCardEnabled(true).build();
    }

}
```


```python
class Car:<br>
    def __init__(self, make=None, model=None, color=None, engine=None):<br>
        self.make = make
        self.model = model
        self.color = color
        self.engine = engine

    def __str__(self):
        return f"Car(make={self.make}, model={self.model}, color={self.color}, engine={self.engine})"

class CarBuilder:
    def __init__(self):
        self.car = Car()

    def set_make(self, make):
        self.car.make = make
        return self

    def set_model(self, model):
        self.car.model = model
        return self

    def set_color(self, color):
        self.car.color = color
        return self

    def set_engine(self, engine):
        self.car.engine = engine
        return self

    def build(self):
        return self.car

# Using the CarBuilder to create different configurations of Car<br>
builder = CarBuilder()<br>
car1 = builder.set_make("Toyota").set_model("Camry").set_color("Red").set_engine("Hybrid").build()<br>
car2 = builder.set_make("Tesla").set_model("Model S").set_color("White").set_engine("Electric").build()<br><br>

print(car1)  # Output: Car(make=Toyota, model=Camry, color=Red, engine=Hybrid)<br>
print(car2)  # Output: Car(make=Tesla, model=Model S, color=White, engine=Electric)<br>
```

<p><strong>Example with a Complex Object</strong></p>

```python
class Computer:
    def __init__(self, cpu=None, ram=None, storage=None, graphics_card=None, os="Linux"):
        self.cpu = cpu
        self.ram = ram
        self.storage = storage
        self.graphics_card = graphics_card
        self.os = os

    def __str__(self):
        return f"Computer(cpu={self.cpu}, ram={self.ram}, storage={self.storage}, graphics_card={self.graphics_card}, os={self.os})"

class ComputerBuilder:
    def __init__(self):
        self.computer = Computer()

    def set_cpu(self, cpu):
        self.computer.cpu = cpu
        return self

    def set_ram(self, ram):
        self.computer.ram = ram
        return self

    def set_storage(self, storage):
        self.computer.storage = storage
        return self

    def set_graphics_card(self, graphics_card):
        self.computer.graphics_card = graphics_card
        return self

    def set_os(self, os):
        self.computer.os = os
        return self

    def build(self):
        return self.computer

# Using ComputerBuilder to create different configurations of Computer
builder = ComputerBuilder()
gaming_pc = builder.set_cpu("Intel i9").set_ram("32GB").set_storage("1TB SSD").set_graphics_card("NVIDIA RTX 3080").build()
office_pc = builder.set_cpu("Intel i5").set_ram("16GB").set_storage("512GB SSD").build()

print(gaming_pc)  # Output: Computer(cpu=Intel i9, ram=32GB, storage=1TB SSD, graphics_card=NVIDIA RTX 3080, os=Linux)
print(office_pc)  # Output: Computer(cpu=Intel i5, ram=16GB, storage=512GB SSD, graphics_card=None, os=Linux)

```


<br>
<br>

<h3>Prototype Design Pattern</h3>
<p>The <strong>Prototype Design Pattern</strong> is a <strong>creational design pattern</strong> that helps in creating new objects by <strong>copying (or "cloning") an existing object</strong>, which serves as a prototype. Instead of building an object from scratch, we create a duplicate of an existing instance, which can then be modified as needed. This can be especially helpful if creating new instances of a class is resource-intensive.</p>

<strong>1. Advantages for Developers</strong>
<ul>
    <li><strong>Performance Improvement</strong>: Cloning objects is faster than creating new ones from scratch, especially if object creation is costly or complex.</li>
    <li><strong>Reduced Complexity</strong>: Simplifies object creation, especially when many configurations or states are involved.</li>
    <li><strong>Easily Adjustable</strong>: Developers can create a base object and modify it on the fly, which reduces code redundancy.</li>
    <li><strong>Memory Efficient</strong>: Only the necessary objects are created instead of creating multiple similar instances.</li>
</ul>

<strong>2. When to Use the Prototype Pattern</strong>
<ul>
    <li>When <strong>object creation is expensive</strong> (e.g., initializing complex objects).</li>
    <li>When the objects to be created are <strong>similar</strong> but require slight adjustments.</li>
    <li>When <strong>creating a large number of identical or nearly identical objects</strong> is needed.</li>
    <li>When <strong>runtime flexibility</strong> is required to add new types without altering existing code.</li>
</ul>

<strong>3. Real-time Analogy</strong>
<p>Think of <strong>copying a template document</strong>. You have a template that already has a format, design, and structure. Rather than creating a new document from scratch each time, you just make a copy, adjust some details (like the name and date), and save it. This is quicker and more convenient than building a new document each time.</p>

<strong>4. Real-time Applications</strong>
<ul>
    <li><strong>Game Development</strong>: Quickly creating similar objects (like multiple enemy types).</li>
    <li><strong>GUI Development</strong>: Cloning pre-built templates with pre-defined elements.</li>
    <li><strong>Document Management</strong>: Creating documents from a standard template.</li>
    <li><strong>Database Records</strong>: Cloning prototype records when adding new entries that resemble existing ones.</li>
</ul>

<strong>5. Steps to Implement the Prototype Pattern</strong>
<ol>
    <li><strong>Create a Prototype Interface or Class</strong>: Define a <code>clone</code> method for cloning objects.</li>
    <li><strong>Implement Concrete Prototype Classes</strong>: Create classes that implement the <code>clone</code> method, defining how objects will be cloned.</li>
    <li><strong>Client Code</strong>: The client uses the <code>clone</code> method to duplicate objects instead of creating them anew.</li>
</ol>

<strong>6. Examples in Python</strong>

<p><strong>Example 1: Basic Prototype</strong></p>

```python
import copy

# Step 1: Define a Prototype Class with a clone method
class Prototype:
    def clone(self):
        return copy.deepcopy(self)

# Step 2: Create a Concrete Prototype
class Car(Prototype):
    def __init__(self, model, color, price):
        self.model = model
        self.color = color
        self.price = price

    def __str__(self):
        return f"Car(model={self.model}, color={self.color}, price={self.price})"

# Step 3: Client Code to Clone
car1 = Car("Sedan", "Blue", 20000)
print("Original Car:", car1)

# Cloning the original car and modifying the clone
car2 = car1.clone()
car2.color = "Red"
car2.price = 25000
print("Cloned Car:", car2)

```

<p>In this example, <code>car2</code> is a copy of <code>car1</code> but with a different color and price. Both objects are independent.</p>

<p><strong>Example 2: Prototype with Configuration</strong></p>

```python
class HousePrototype(Prototype):
    def __init__(self, floors, rooms, has_garden):
        self.floors = floors
        self.rooms = rooms
        self.has_garden = has_garden

    def __str__(self):
        return f"House(floors={self.floors}, rooms={self.rooms}, has_garden={self.has_garden})"

# Client code to clone
house1 = HousePrototype(floors=2, rooms=4, has_garden=True)
print("Original House:", house1)

# Clone and customize
house2 = house1.clone()
house2.floors = 3  # Modified clone with additional floor
print("Cloned House:", house2)

```

<p>In this example, <code>house2</code> starts as a clone of <code>house1</code> but adds an extra floor after cloning, creating a unique instance with minimal effort.</p>

<strong>Summary</strong>
<p>The Prototype pattern helps you <strong>reuse existing instances</strong> as a blueprint for creating new ones, making development faster and more memory-efficient. This pattern is handy for scenarios where creating new instances is complex or costly.</p>

