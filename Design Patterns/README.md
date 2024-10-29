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


