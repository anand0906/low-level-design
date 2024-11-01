<h1>Behavioural Design Pattern</h1>
<p><strong>Behavioral Design Patterns</strong> are design patterns that help with communication and interaction between objects in a software system. They focus on how objects cooperate and how responsibilities are assigned between them to make a system more flexible, efficient, and easier to maintain.</p>

<p><strong>Key Characteristics of Behavioral Design Patterns:</strong></p>
<ul>
    <li><strong>Define Communication Rules</strong>: These patterns set up "rules" for how objects should interact with each other.</li>
    <li><strong>Promote Loose Coupling</strong>: Behavioral patterns often reduce the dependency between objects, making the code easier to modify or extend.</li>
    <li><strong>Distribute Responsibility</strong>: They help in organizing the distribution of tasks and responsibilities, so each part of the system is clear in its role.</li>
</ul>

<p><strong>Common Behavioral Design Patterns</strong></p>
<ol>
    <li><strong>Strategy</strong></li>
    <li><strong>Observer</strong></li>
    <li><strong>Command</strong></li>
    <li><strong>State</strong></li>
    <li><strong>Chain of Responsibility</strong></li>
    <li><strong>Iterator</strong></li>
    <li><strong>Template Method</strong></li>
</ol>

<h2>Strategy Design Pattern</h2>
<p><strong>Strategy Design Pattern</strong></p>

<p>The Strategy Pattern is a behavioral design pattern that allows you to define a family of algorithms, put each of them into a separate class, and make their objects interchangeable. This pattern enables a client to choose an algorithm from a family of algorithms at runtime and change it as needed.</p>

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240209100509/Strategy-Design-Pattern.webp">

<p><strong>Key Characteristics of the Strategy Pattern</strong></p>
<ul>
    <li><strong>Encapsulates Algorithms</strong>: Each algorithm is placed in its own class, making it easy to add new strategies without modifying existing code.</li>
    <li><strong>Flexible Behavior</strong>: Clients can change the algorithm they use dynamically, allowing for adaptable behavior.</li>
    <li><strong>Single Responsibility</strong>: Keeps each algorithm focused on a specific task, making the code more modular and maintainable.</li>
</ul>

<p><strong>Why Use the Strategy Pattern?</strong></p>
<p>Use the Strategy Pattern when:</p>
<ul>
    <li>There are multiple ways to perform an action, and the algorithm can change depending on the situation.</li>
    <li>You want to avoid multiple conditional statements and allow easier algorithm extension and maintenance.</li>
    <li>Behavior needs to vary independently of the main logic, enabling easy swapping of algorithms at runtime.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Imagine a transportation app that offers different travel options (like driving, cycling, and walking) to get from one place to another. The app lets users choose the most suitable route based on their preference. Each transportation method is a separate strategy, and the app allows users to switch between them seamlessly.</p>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Strategy Interface</strong>: Declares the method that all strategies must implement.</li>
    <li><strong>Concrete Strategy</strong>: Implements specific algorithms following the strategy interface.</li>
    <li><strong>Context</strong>: Maintains a reference to a strategy object and delegates the algorithm to the strategy instance.</li>
</ol>

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240209100509/Strategy-Design-Pattern.webp">

<p><strong>Steps to Implement the Strategy Pattern</strong></p>
<ol>
    <li>Create a <strong>Strategy Interface</strong> that defines the common method for all algorithms.</li>
    <li>Implement each <strong>Concrete Strategy</strong> that follows the Strategy Interface and provides its own specific algorithm.</li>
    <li>Create a <strong>Context</strong> class that uses a strategy object and delegates the execution to that object.</li>
    <li>In the <strong>Client Code</strong>, choose a strategy based on the current needs and set it in the context.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example of the Strategy Pattern in Python, where different discount strategies are applied in a shopping cart:</p>

```python
from abc import ABC, abstractmethod

# Strategy Interface
class DiscountStrategy(ABC):
    @abstractmethod
    def calculate_discount(self, price):
        pass

# Concrete Strategy: Percentage Discount
class PercentageDiscount(DiscountStrategy):
    def __init__(self, percentage):
        self.percentage = percentage

    def calculate_discount(self, price):
        return price * (1 - self.percentage / 100)

# Concrete Strategy: Flat Discount
class FlatDiscount(DiscountStrategy):
    def __init__(self, amount):
        self.amount = amount

    def calculate_discount(self, price):
        return price - self.amount

# Context: Shopping Cart
class ShoppingCart:
    def __init__(self, strategy: DiscountStrategy):
        self.strategy = strategy

    def apply_discount(self, price):
        return self.strategy.calculate_discount(price)

# Client Code
def main():
    price = 100.0

    # Use Percentage Discount Strategy
    percentage_discount = PercentageDiscount(10)
    cart1 = ShoppingCart(percentage_discount)
    print("Total after percentage discount:", cart1.apply_discount(price))

    # Use Flat Discount Strategy
    flat_discount = FlatDiscount(15)
    cart2 = ShoppingCart(flat_discount)
    print("Total after flat discount:", cart2.apply_discount(price))

if __name__ == "__main__":
    main()
```
<p><strong>Explanation</strong>:</p>
<ul>
    <li>The <strong>DiscountStrategy</strong> interface defines the method for calculating discounts.</li>
    <li><strong>PercentageDiscount</strong> and <strong>FlatDiscount</strong> are specific strategies implementing different discount methods.</li>
    <li>The <strong>ShoppingCart</strong> class holds a reference to a discount strategy and applies it when calculating the total.</li>
</ul>

<p><strong>More Examples</strong></p>
<ul>
    <li><strong>Sorting Algorithms</strong>: A program that can switch between sorting algorithms (like quicksort, mergesort) based on data size or type.</li>
    <li><strong>Payment Methods</strong>: An e-commerce site might offer different payment methods like credit card, PayPal, and cryptocurrency as separate strategies.</li>
    <li><strong>Tax Calculations</strong>: A business application can use different tax calculation strategies based on location.</li>
</ul>

<p>The Strategy Pattern makes a system more flexible, allowing it to switch between algorithms at runtime and promoting cleaner, more modular code.</p>


<br>
<br>

<h2>Iterator Design Pattern</h2>
<p><strong>Iterator Design Pattern</strong></p>

<p>The Iterator Pattern is a behavioral design pattern that provides a way to access elements of a collection (such as lists, arrays, or custom collections) sequentially, without exposing the underlying structure of the collection. It allows you to iterate over a collection’s elements one by one in a standardized way.</p>

<p><strong>Key Characteristics of the Iterator Pattern</strong></p>
<ul>
    <li><strong>Uniform Access</strong>: Allows access to elements in a collection without revealing its underlying implementation.</li>
    <li><strong>Sequential Access</strong>: Accesses elements one at a time, simplifying the process of working with collections.</li>
    <li><strong>Multiple Iterations</strong>: Enables multiple iterators to work on the same collection independently.</li>
</ul>

<p><strong>Why Use the Iterator Pattern?</strong></p>
<p>Use the Iterator Pattern when:</p>
<ul>
    <li>You have a collection of objects, and you want a consistent way to access each element without needing to understand the collection’s internal structure.</li>
    <li>You need to support multiple types of iteration, such as reverse or conditional traversal, for the same collection.</li>
    <li>You want to provide an easy way to traverse custom data structures without exposing their internal implementation.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Imagine a playlist of songs. The Iterator Pattern is like having a "next" and "previous" button on your music player, allowing you to move through songs one by one without knowing how the playlist is stored. You simply move from one song to the next in a consistent order.</p>

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240401123215/Iterator-design-pattern.webp">

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Iterator Interface</strong>: Declares the operations required for traversing a collection, such as <code>next()</code> and <code>has_next()</code>.</li>
    <li><strong>Concrete Iterator</strong>: Implements the iterator interface and tracks the current position in the collection.</li>
    <li><strong>Collection Interface</strong>: Declares a method to return an iterator for the collection.</li>
    <li><strong>Concrete Collection</strong>: Implements the collection interface and returns a concrete iterator for itself.</li>
</ol>

<p><strong>Steps to Implement the Iterator Pattern</strong></p>
<ol>
    <li>Define an <strong>Iterator Interface</strong> with methods for traversing elements, like <code>next()</code> and <code>has_next()</code>.</li>
    <li>Implement a <strong>Concrete Iterator</strong> that keeps track of the current position in the collection and provides methods to access elements.</li>
    <li>Create a <strong>Collection Interface</strong> with a method to return an iterator.</li>
    <li>Implement a <strong>Concrete Collection</strong> that provides an iterator.</li>
    <li>Use the <strong>Client Code</strong> to iterate over the collection using the iterator, without needing to understand its structure.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example in Python demonstrating the Iterator Pattern for a collection of book titles:</p>

```python
class Book:
    def __init__(self, title):
        self.title = title

class BookIterator:
    def __init__(self, books):
        self._books = books
        self._index = 0

    def __next__(self):
        if self._index >= len(self._books):
            raise StopIteration
        book = self._books[self._index]
        self._index += 1
        return book.title

    def has_next(self):
        return self._index < len(self._books)

class BookCollection:
    def __init__(self):
        self._books = []

    def add_book(self, book):
        self._books.append(book)

    def __iter__(self):
        return BookIterator(self._books)

# Client Code
def main():
    collection = BookCollection()
    collection.add_book(Book("1984"))
    collection.add_book(Book("Brave New World"))
    collection.add_book(Book("Fahrenheit 451"))

    # Use the iterator to go through the books
    for book in collection:
        print("Book title:", book)

if __name__ == "__main__":
    main()
```

<p><strong>Explanation</strong>:</p>
<ul>
    <li>The <strong>BookIterator</strong> class provides a way to iterate over the collection of books.</li>
    <li>The <strong>BookCollection</strong> class has a method to return an iterator for itself, which allows us to use the iterator in a <code>for</code> loop.</li>
    <li>The <strong>Client Code</strong> uses the iterator to print out each book title in the collection.</li>
</ul>

<p><strong>More Examples</strong></p>
<ul>
    <li><strong>Browsing History</strong>: An iterator could be used to go through the browsing history without needing to know how it’s stored.</li>
    <li><strong>File System</strong>: File iterators can allow traversal of files and directories in a specific order, abstracting the details of file structure.</li>
    <li><strong>Database Results</strong>: An iterator can be used to iterate through query results without needing to load everything into memory at once.</li>
</ul>

<p>The Iterator Pattern simplifies access to elements in a collection, making it easier to work with complex data structures and allowing for flexibility in how data is processed.</p>

<br>
<br>

<h2>Observer Design Pattern</h2>
<p><strong>Observer Design Pattern</strong></p>

<p>The Observer Pattern is a behavioral design pattern where an object, called the <strong>Subject</strong>, maintains a list of dependents, called <strong>Observers</strong>, and notifies them of any state changes. This pattern is useful for establishing a one-to-many relationship between objects, allowing a subject to automatically update observers when something changes.</p>

<p><strong>Key Characteristics of the Observer Pattern</strong></p>
<ul>
    <li><strong>One-to-Many Dependency</strong>: Changes in one object (the subject) automatically notify and update all dependent objects (observers).</li>
    <li><strong>Loose Coupling</strong>: Observers and subjects interact through a common interface, making it easy to add or remove observers without affecting the subject.</li>
    <li><strong>Dynamic Updates</strong>: Observers can be dynamically added or removed, allowing flexibility in response to changes.</li>
</ul>

<p><strong>Why Use the Observer Pattern?</strong></p>
<p>Use the Observer Pattern when:</p>
<ul>
    <li>Changes in one object need to trigger updates in other objects, but you don’t want these objects to be tightly coupled.</li>
    <li>Multiple parts of a system need to react to changes in the same data or state.</li>
    <li>You want to provide a way to subscribe to or unsubscribe from updates dynamically.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Imagine a news subscription service. Whenever there’s a breaking news update, all subscribed users (observers) are notified with the latest information. The news service (subject) doesn’t need to know about the individual subscribers; it simply notifies them when there’s an update, and they all receive the information.</p>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Subject Interface</strong>: Declares methods to attach, detach, and notify observers.</li>
    <li><strong>Concrete Subject</strong>: Maintains a list of observers and implements methods to notify them of changes.</li>
    <li><strong>Observer Interface</strong>: Declares the update method, which is called by the subject when its state changes.</li>
    <li><strong>Concrete Observer</strong>: Implements the observer interface and defines how to respond to updates.</li>
</ol>

<p><strong>Steps to Implement the Observer Pattern</strong></p>
<ol>
    <li>Create an <strong>Observer Interface</strong> with an update method for receiving updates from the subject.</li>
    <li>Implement a <strong>Concrete Observer</strong> that follows the observer interface and defines how it should react to updates.</li>
    <li>Define a <strong>Subject Interface</strong> with methods to attach, detach, and notify observers.</li>
    <li>Implement a <strong>Concrete Subject</strong> that maintains a list of observers and notifies them when its state changes.</li>
    <li>Use the <strong>Client Code</strong> to add or remove observers from the subject and trigger updates.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example in Python demonstrating the Observer Pattern for a weather station that notifies observers of temperature changes:</p>

```python
from abc import ABC, abstractmethod

# Observer Interface
class Observer(ABC):
    @abstractmethod
    def update(self, temperature):
        pass

# Concrete Observer: Display
class TemperatureDisplay(Observer):
    def update(self, temperature):
        print(f"Temperature Display: The temperature is now {temperature}°C")

# Concrete Observer: Alert
class TemperatureAlert(Observer):
    def update(self, temperature):
        if temperature > 30:
            print("Temperature Alert: Temperature is above 30°C! Warning!")
        else:
            print("Temperature Alert: Temperature is safe.")

# Subject Interface
class Subject(ABC):
    @abstractmethod
    def attach(self, observer):
        pass

    @abstractmethod
    def detach(self, observer):
        pass

    @abstractmethod
    def notify(self):
        pass

# Concrete Subject: Weather Station
class WeatherStation(Subject):
    def __init__(self):
        self._observers = []
        self._temperature = 0

    def attach(self, observer):
        self._observers.append(observer)

    def detach(self, observer):
        self._observers.remove(observer)

    def set_temperature(self, temperature):
        self._temperature = temperature
        self.notify()

    def notify(self):
        for observer in self._observers:
            observer.update(self._temperature)

# Client Code
def main():
    # Create subject
    weather_station = WeatherStation()

    # Create observers
    display = TemperatureDisplay()
    alert = TemperatureAlert()

    # Attach observers
    weather_station.attach(display)
    weather_station.attach(alert)

    # Change temperature and notify observers
    weather_station.set_temperature(28)
    weather_station.set_temperature(35)

if __name__ == "__main__":
    main()
```

<p><strong>Explanation</strong>:</p>
<ul>
    <li>The <strong>WeatherStation</strong> class is the subject that maintains a list of observers and notifies them of temperature changes.</li>
    <li>The <strong>TemperatureDisplay</strong> and <strong>TemperatureAlert</strong> classes are concrete observers that define how to respond to updates.</li>
    <li>The <strong>Client Code</strong> attaches observers to the subject, and they receive updates whenever the temperature changes.</li>
</ul>

<p><strong>More Examples</strong></p>
<ul>
    <li><strong>Social Media Notifications</strong>: Followers are notified when someone they follow posts a new update.</li>
    <li><strong>Stock Market Tracker</strong>: Investors are notified whenever there are significant changes in stock prices.</li>
    <li><strong>Chat Application</strong>: Users in a chat room receive notifications when someone sends a message.</li>
</ul>

<p>The Observer Pattern allows objects to stay updated with changes without tightly coupling them, making it ideal for systems that need flexible and dynamic communication among components.</p>


<br>
<br>

<h2>Template Method Design Pattern</h2>
<p><strong>Template Method Design Pattern</strong></p>

<p>The Template Method Pattern is a behavioral design pattern that defines the structure (or “template”) of an algorithm in a superclass, while allowing subclasses to implement specific steps. This pattern lets you define an algorithm's framework in a method and delegate some of its steps to subclasses, promoting reuse and code consistency.</p>

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240213152828/Untitled-Diagram.webp">

<p><strong>Key Characteristics of the Template Method Pattern</strong></p>
<ul>
    <li><strong>Defines Algorithm Structure</strong>: Provides a skeleton of the steps of an algorithm, leaving the details to subclasses.</li>
    <li><strong>Encourages Code Reuse</strong>: Shared code for common steps lives in the superclass, while subclasses only implement the unique parts.</li>
    <li><strong>Template Method</strong>: The main method in the superclass that defines the order of the steps.</li>
</ul>

<p><strong>Why Use the Template Method Pattern?</strong></p>
<p>Use the Template Method Pattern when:</p>
<ul>
    <li>You have an algorithm that can mostly be shared across subclasses but needs some parts customized by each subclass.</li>
    <li>You want to avoid duplicating code across subclasses by putting shared behavior in a superclass.</li>
    <li>You need to enforce an algorithm structure while allowing customization in specific steps.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Imagine a coffee shop that makes different types of coffee drinks. Every coffee drink follows a similar process: boil water, brew the coffee, pour it into a cup, and add condiments. The type of condiment can vary (milk, sugar, etc.), but the general process is the same. The Template Method Pattern allows us to outline the steps of making coffee while letting each subclass specify which condiment to add.</p>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Abstract Class</strong>: Defines the template method (the main algorithm) and declares abstract methods for customizable steps.</li>
    <li><strong>Template Method</strong>: The method in the abstract class that outlines the steps of the algorithm and calls specific steps, some of which are defined by subclasses.</li>
    <li><strong>Concrete Class</strong>: Implements the abstract steps defined by the abstract class, providing custom behavior for each step.</li>
</ol>

<p><strong>Steps to Implement the Template Method Pattern</strong></p>
<ol>
    <li>Create an <strong>Abstract Class</strong> that defines a template method, laying out the structure of the algorithm.</li>
    <li>In the abstract class, define abstract or hook methods for steps that will be implemented or modified by subclasses.</li>
    <li>Implement <strong>Concrete Classes</strong> that override the abstract methods to customize specific steps.</li>
    <li>Use the <strong>Client Code</strong> to call the template method on different concrete classes.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example in Python using the Template Method Pattern to make different types of coffee:</p>

```python
from abc import ABC, abstractmethod

# Abstract Class
class CoffeeTemplate(ABC):
    def make_coffee(self):
        self.boil_water()
        self.brew_coffee()
        self.pour_in_cup()
        self.add_condiments()

    def boil_water(self):
        print("Boiling water")

    def pour_in_cup(self):
        print("Pouring into cup")

    @abstractmethod
    def brew_coffee(self):
        pass

    @abstractmethod
    def add_condiments(self):
        pass

# Concrete Class: Black Coffee
class BlackCoffee(CoffeeTemplate):
    def brew_coffee(self):
        print("Brewing black coffee")

    def add_condiments(self):
        print("Adding sugar")

# Concrete Class: Latte
class Latte(CoffeeTemplate):
    def brew_coffee(self):
        print("Brewing coffee for latte")

    def add_condiments(self):
        print("Adding milk")

# Client Code
def main():
    print("Making Black Coffee:")
    black_coffee = BlackCoffee()
    black_coffee.make_coffee()

    print("\nMaking Latte:")
    latte = Latte()
    latte.make_coffee()

if __name__ == "__main__":
    main()
```

<p><strong>Explanation</strong>:</p>
<ul>
    <li>The <strong>CoffeeTemplate</strong> class defines the template method <code>make_coffee()</code>, which outlines the steps for making coffee.</li>
    <li><strong>BlackCoffee</strong> and <strong>Latte</strong> are concrete classes that customize specific steps, such as <code>brew_coffee()</code> and <code>add_condiments()</code>.</li>
    <li>The <strong>Client Code</strong> calls <code>make_coffee()</code> on each concrete class to prepare different coffee types using the same general process.</li>
</ul>

<p><strong>More Examples</strong></p>
<ul>
    <li><strong>Document Generation</strong>: Different types of documents (PDF, Word) follow similar steps to create but have specific formatting options.</li>
    <li><strong>Data Processing</strong>: Data processing workflows may have shared steps (load, process, export) but customized processing logic for different data types.</li>
    <li><strong>Game AI</strong>: The Template Method Pattern can be used to define general behaviors for different enemy types, allowing each subclass to modify specific actions.</li>
</ul>

<p>The Template Method Pattern promotes code reuse, enforces an algorithm structure, and makes it easier to define variations in subclasses without modifying the base algorithm.</p>

<br>
<br>

<h2>Command Design Pattern</h2>
<p><strong>Command Design Pattern</strong></p>

<p>The Command Pattern is a behavioral design pattern that turns a request into a stand-alone object containing all the information about the request, making it easier to parameterize actions, queue them, and perform undo operations. It separates the object that invokes an operation from the one that knows how to execute it, enabling more flexible and decoupled code.</p>

<p><strong>Key Characteristics of the Command Pattern</strong></p>
<ul>
    <li><strong>Encapsulates Actions as Objects</strong>: Actions are encapsulated as command objects, allowing for easy manipulation and reuse.</li>
    <li><strong>Decouples Invokers from Executors</strong>: The sender of the request doesn’t need to know the details of how the command is executed.</li>
    <li><strong>Supports Undoable Operations</strong>: Allows the implementation of undo/redo functionality by storing executed commands.</li>
</ul>

<p><strong>Why Use the Command Pattern?</strong></p>
<p>Use the Command Pattern when:</p>
<ul>
    <li>You need to parameterize objects with operations or handle operations as first-class objects.</li>
    <li>You want to queue, log, or schedule operations, such as in task scheduling or batch processing.</li>
    <li>You need to implement undo/redo functionality in an application, which requires storing and reversing executed actions.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Consider a remote control for a television. Each button on the remote represents a command (like turning the TV on, off, or adjusting the volume). The remote doesn’t know how the TV performs these actions—it simply sends the command. The TV handles each command based on the request, making it easy to add more commands as needed.</p>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Command Interface</strong>: Declares a method for executing a command.</li>
    <li><strong>Concrete Command</strong>: Implements the command interface, containing the code to perform specific actions.</li>
    <li><strong>Invoker</strong>: Initiates a request to execute a command, but doesn’t know how the command is executed.</li>
    <li><strong>Receiver</strong>: Knows how to carry out the request and performs the actual work when a command is executed.</li>
    <li><strong>Client</strong>: Creates and configures the command objects, associating them with the invoker and receiver.</li>
</ol>

<p><strong>Steps to Implement the Command Pattern</strong></p>
<ol>
    <li>Create a <strong>Command Interface</strong> with an <code>execute()</code> method.</li>
    <li>Define one or more <strong>Concrete Commands</strong> that implement the command interface and call specific actions on the receiver.</li>
    <li>Create a <strong>Receiver</strong> class that knows how to perform the requested actions.</li>
    <li>Implement an <strong>Invoker</strong> class that holds a command and calls its <code>execute()</code> method.</li>
    <li>Use the <strong>Client Code</strong> to associate commands with the invoker and receiver.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example in Python demonstrating the Command Pattern with a light switch system:</p>

```python
from abc import ABC, abstractmethod

# Command Interface
class Command(ABC):
    @abstractmethod
    def execute(self):
        pass

# Receiver
class Light:
    def turn_on(self):
        print("The light is on")

    def turn_off(self):
        print("The light is off")

# Concrete Command: Turn On
class TurnOnCommand(Command):
    def __init__(self, light):
        self.light = light

    def execute(self):
        self.light.turn_on()

# Concrete Command: Turn Off
class TurnOffCommand(Command):
    def __init__(self, light):
        self.light = light

    def execute(self):
        self.light.turn_off()

# Invoker
class RemoteControl:
    def __init__(self):
        self.command = None

    def set_command(self, command):
        self.command = command

    def press_button(self):
        if self.command:
            self.command.execute()

# Client Code
def main():
    # Create receiver
    light = Light()

    # Create commands
    turn_on = TurnOnCommand(light)
    turn_off = TurnOffCommand(light)

    # Create invoker
    remote = RemoteControl()

    # Turn the light on
    remote.set_command(turn_on)
    remote.press_button()

    # Turn the light off
    remote.set_command(turn_off)
    remote.press_button()

if __name__ == "__main__":
    main()
```

<p><strong>Explanation</strong>:</p>
<ul>
    <li>The <strong>Light</strong> class is the receiver, which knows how to turn itself on and off.</li>
    <li><strong>TurnOnCommand</strong> and <strong>TurnOffCommand</strong> are concrete commands that implement the <code>execute()</code> method to turn the light on and off, respectively.</li>
    <li><strong>RemoteControl</strong> is the invoker, responsible for holding a command and triggering its execution when the button is pressed.</li>
    <li>The <strong>Client Code</strong> configures commands and sends them to the invoker, controlling the light without needing to understand the details of how it works.</li>
</ul>

<p><strong>More Examples</strong></p>
<ul>
    <li><strong>Text Editor</strong>: Each command (copy, paste, undo) is represented as a separate command object that can be stored in a history for undo functionality.</li>
    <li><strong>Job Scheduling</strong>: Commands represent tasks in a queue, executed one after another, like in cron jobs or background tasks.</li>
    <li><strong>Database Transactions</strong>: Each transaction operation (commit, rollback) can be encapsulated as a command to allow reversing of actions if necessary.</li>
</ul>

<p>The Command Pattern is helpful for decoupling requests from execution, making code flexible and adaptable, especially when implementing queuing, undo, and logging functionalities.</p>


<br>
<br>

<h2>State Design Pattern</h2>
<p><strong>State Design Pattern</strong></p>

<p>The State Pattern is a behavioral design pattern that allows an object to change its behavior when its internal state changes. The object will appear to change its class, enabling it to exhibit different behaviors depending on its current state. This pattern is particularly useful for managing state transitions without relying on complex conditional statements.</p>

<p><strong>Key Characteristics of the State Pattern</strong></p>
<ul>
    <li><strong>Encapsulates State-Specific Behavior</strong>: Each state is represented by a separate class, which implements the behavior associated with that state.</li>
    <li><strong>Reduces Conditional Complexity</strong>: Eliminates the need for complex if-else or switch-case statements by delegating state-specific behavior to state classes.</li>
    <li><strong>Dynamic State Change</strong>: The context object can change its state dynamically, altering its behavior at runtime.</li>
</ul>

<p><strong>Why Use the State Pattern?</strong></p>
<p>Use the State Pattern when:</p>
<ul>
    <li>An object can be in multiple states, and its behavior should change based on its current state.</li>
    <li>You want to avoid large amounts of conditional logic that dictate behavior based on the state of an object.</li>
    <li>You need to implement state-dependent behavior that can change dynamically at runtime.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Consider a music player application. The music player can be in different states such as Playing, Paused, or Stopped. Each state will dictate different behaviors (like play, pause, or stop). The player should change its behavior based on the current state without requiring complex conditions to check its state.</p>

<p>You can also apply this approach to objects. Imagine that we have a Document class. A document can be in one of three states: Draft, Moderation and Published. The publish method of the document works a little bit differently in each state:</p>

<ul>
	<li>In Draft, it moves the document to moderation.</li>
	<li>In Moderation, it makes the document public, but only if the current user is an administrator.</li>
	<li>In Published, it doesn’t do anything at al</li>
</ul>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Context</strong>: The class that has a state and delegates state-specific behavior to the current state object.</li>
    <li><strong>State Interface</strong>: Defines the interface for state-specific behavior.</li>
    <li><strong>Concrete States</strong>: Classes that implement the state interface and define behavior for specific states.</li>
</ol>

<p><strong>Steps to Implement the State Pattern</strong></p>
<ol>
    <li>Create a <strong>State Interface</strong> that defines methods for state-specific behavior.</li>
    <li>Implement <strong>Concrete State Classes</strong> that represent specific states and implement the state interface.</li>
    <li>Create a <strong>Context Class</strong> that holds a reference to a current state and delegates behavior to that state.</li>
    <li>Implement methods in the context to change the current state.</li>
    <li>Use the <strong>Client Code</strong> to create the context and change its state as needed.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example in Python demonstrating the State Pattern with a simple music player:</p>

```python
from abc import ABC, abstractmethod

# State Interface
class State(ABC):
    @abstractmethod
    def press_play(self):
        pass

    @abstractmethod
    def press_pause(self):
        pass

# Concrete State: Playing
class PlayingState(State):
    def press_play(self):
        print("Already playing.")

    def press_pause(self):
        print("Pausing the music.")
        # Transition to paused state

# Concrete State: Paused
class PausedState(State):
    def press_play(self):
        print("Resuming the music.")
        # Transition to playing state

    def press_pause(self):
        print("Already paused.")

# Context
class MusicPlayer:
    def __init__(self):
        self.state = PlayingState()  # Default state

    def set_state(self, state):
        self.state = state

    def press_play(self):
        self.state.press_play()

    def press_pause(self):
        self.state.press_pause()

# Client Code
def main():
    player = MusicPlayer()

    player.press_play()  # Output: Already playing.
    player.set_state(PausedState())  # Change state to paused
    player.press_play()  # Output: Resuming the music.
    player.press_pause()  # Output: Pausing the music.

if __name__ == "__main__":
    main()
```

<p><strong>Explanation</strong>:</p>
<ul>
    <li>The <strong>State</strong> interface defines the methods that all concrete states must implement.</li>
    <li><strong>PlayingState</strong> and <strong>PausedState</strong> are concrete states that implement behavior specific to each state.</li>
    <li>The <strong>MusicPlayer</strong> class is the context that holds the current state and delegates actions to the current state.</li>
    <li>The <strong>Client Code</strong> demonstrates how to change the state of the music player and perform actions based on its state.</li>
</ul>

<p><strong>State Design Pattern Example: Document Class</strong></p>

<p>In this example, we will create a <strong>Document</strong> class that can be in one of three states: Draft, Moderation, and Published. Each state will have a different behavior for the <code>publish()</code> method.</p>

<p><strong>Key Components:</strong></p>
<ul>
    <li><strong>State Interface</strong>: Defines the interface for state-specific behavior.</li>
    <li><strong>Concrete States</strong>: Classes that implement the state interface for each specific state (Draft, Moderation, Published).</li>
    <li><strong>Context Class</strong>: The Document class that holds a reference to the current state and delegates the <code>publish()</code> method to the current state.</li>
</ul>

```python
from abc import ABC, abstractmethod

# State Interface
class DocumentState(ABC):
    @abstractmethod
    def publish(self, document, user):
        pass

# Concrete State: Draft
class DraftState(DocumentState):
    def publish(self, document, user):
        print("Document is moving to moderation.")
        document.set_state(ModerationState())

# Concrete State: Moderation
class ModerationState(DocumentState):
    def publish(self, document, user):
        if user.is_admin:
            print("Document is now published.")
            document.set_state(PublishedState())
        else:
            print("Only admins can publish the document from moderation.")

# Concrete State: Published
class PublishedState(DocumentState):
    def publish(self, document, user):
        print("Document is already published. No action taken.")

# Context Class: Document
class Document:
    def __init__(self):
        self.state = DraftState()  # Default state is Draft

    def set_state(self, state):
        self.state = state

    def publish(self, user):
        self.state.publish(self, user)

# User Class
class User:
    def __init__(self, is_admin):
        self.is_admin = is_admin

# Client Code
def main():
    # Create a user (not an admin)
    user1 = User(is_admin=False)
    document = Document()

    print("User 1 publishing document:")
    document.publish(user1)  # Output: Document is moving to moderation.

    # Create a user (admin)
    user2 = User(is_admin=True)
    print("\nUser 2 publishing document:")
    document.publish(user2)  # Output: Document is now published.

    print("\nUser 2 trying to publish again:")
    document.publish(user2)  # Output: Document is already published. No action taken.

if __name__ == "__main__":
    main()
```

<p><strong>Explanation:</strong></p>
<ul>
    <li>The <strong>DocumentState</strong> interface defines the <code>publish()</code> method, which each concrete state must implement.</li>
    <li>The <strong>DraftState</strong> class changes the state of the document to <strong>ModerationState</strong> when <code>publish()</code> is called.</li>
    <li>The <strong>ModerationState</strong> class checks if the user is an admin before publishing; if so, it changes the state to <strong>PublishedState</strong>.</li>
    <li>The <strong>PublishedState</strong> class does nothing when <code>publish()</code> is called since the document is already published.</li>
    <li>The <strong>User</strong> class represents a user with an <code>is_admin</code> attribute, which is used to control access to the publish functionality.</li>
</ul>

<p><strong>Output Example:</strong></p>

```python
User 1 publishing document:
Document is moving to moderation.

User 2 publishing document:
Document is now published.

User 2 trying to publish again:
Document is already published. No action taken.
```


<p><strong>More Examples</strong></p>
<ul>
    <li><strong>Document Editor</strong>: Different states can represent whether a document is in draft, review, or published state, dictating available actions.</li>
    <li><strong>Vending Machine</strong>: States can represent whether the machine is waiting for selection, dispensing items, or out of service.</li>
    <li><strong>Game AI</strong>: Different AI behaviors based on game states, such as exploring, attacking, or retreating.</li>
</ul>

<p>The State Pattern helps to manage and organize state-specific behavior efficiently, leading to more maintainable and understandable code by encapsulating behaviors within state classes.</p>


<br>
<br>


<h2>Chain Of Responsibility Design Patterns</h2>
<p><strong>Chain of Responsibility Design Pattern</strong></p>

<p>The Chain of Responsibility is a behavioral design pattern that allows multiple objects to handle a request without the sender needing to know which object will ultimately handle the request. The request is passed along a chain of handlers, each of which can either process the request or pass it to the next handler in the chain. This pattern promotes loose coupling and helps to avoid tight coupling between the request sender and the handlers.</p>

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240220141055/Chain-of-Responsibility-Design-Pattern-.webp">

<p><strong>Key Characteristics of the Chain of Responsibility Pattern</strong></p>
<ul>
    <li><strong>Decouples Sender and Receiver</strong>: The sender of the request does not need to know which handler will process it.</li>
    <li><strong>Dynamic Chain Construction</strong>: The chain of handlers can be modified dynamically at runtime by adding or removing handlers.</li>
    <li><strong>Single Responsibility Principle</strong>: Each handler is responsible for a specific type of request, promoting cleaner and more manageable code.</li>
</ul>

<p><strong>Why Use the Chain of Responsibility Pattern?</strong></p>
<p>Use the Chain of Responsibility Pattern when:</p>
<ul>
    <li>You want to avoid coupling the sender of a request to its receivers.</li>
    <li>You have multiple handlers that can handle a request, but only one should do so.</li>
    <li>You want to add or remove handlers dynamically at runtime.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Consider a customer support system. When a customer submits a request, it might first go to a support representative, who can handle basic issues. If the issue is more complex, it could be escalated to a supervisor, then to a manager, and so on. Each level of support is a handler in the chain, and the request is passed along until it reaches the appropriate handler.</p>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Handler Interface</strong>: Defines a method for handling requests and an optional method for setting the next handler in the chain.</li>
    <li><strong>Concrete Handlers</strong>: Classes that implement the handler interface and define specific behavior for handling requests.</li>
    <li><strong>Client Code</strong>: Sets up the chain of handlers and initiates requests.</li>
</ol>

<p><strong>Steps to Implement the Chain of Responsibility Pattern</strong></p>
<ol>
    <li>Create a <strong>Handler Interface</strong> that declares a method for handling requests.</li>
    <li>Implement <strong>Concrete Handlers</strong> that process requests and optionally pass them to the next handler.</li>
    <li>Create a <strong>Client Class</strong> that configures the chain and sends requests.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example in Python demonstrating the Chain of Responsibility Pattern with a logging system:</p>

```python
class Handler:
    def __init__(self, successor=None):
        self.successor = successor

    def handle_request(self, request):
        if self.successor:
            self.successor.handle_request(request)

class ConsoleHandler(Handler):
    def handle_request(self, request):
        if request == "Console":
            print("Handling request in Console.")
        else:
            super().handle_request(request)

class FileHandler(Handler):
    def handle_request(self, request):
        if request == "File":
            print("Handling request in File.")
        else:
            super().handle_request(request)

class DatabaseHandler(Handler):
    def handle_request(self, request):
        if request == "Database":
            print("Handling request in Database.")
        else:
            super().handle_request(request)

# Client Code
def main():
    # Create handlers
    database_handler = DatabaseHandler()
    file_handler = FileHandler(successor=database_handler)
    console_handler = ConsoleHandler(successor=file_handler)

    # Send requests
    requests = ["Console", "File", "Database", "Email"]
    for request in requests:
        print(f"\nRequest: {request}")
        console_handler.handle_request(request)

if __name__ == "__main__":
    main()
```

<p><strong>Explanation:</strong></p>
<ul>
    <li>The <strong>Handler</strong> class defines the structure for the chain, allowing each handler to have a successor.</li>
    <li><strong>Concrete Handlers</strong> (<strong>ConsoleHandler</strong>, <strong>FileHandler</strong>, and <strong>DatabaseHandler</strong>) implement the handling logic for specific requests.</li>
    <li>The <strong>Client Code</strong> sets up the chain by linking handlers together and sends requests through the chain.</li>
</ul>

<p><strong>Output Example:</strong></p>

```python
Request: Console
Handling request in Console.

Request: File
Handling request in File.

Request: Database
Handling request in Database.

Request: Email
```

<p>No handler for request type Email.</p>

<p>This example illustrates how the Chain of Responsibility Pattern can effectively manage requests in a flexible manner, allowing for easy addition or removal of handlers while maintaining loose coupling between request senders and handlers.</p>


<br>
<br>

<h2>Mediator Design Pattern</h2>

<p>The Mediator Pattern is a behavioral design pattern that allows objects to communicate with each other indirectly through a central mediator object. Instead of each object having to reference and interact directly with each other, they communicate through the mediator, which handles the communication and control flow. This pattern promotes loose coupling, making it easier to manage and maintain the interactions between objects.</p>

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240213133020/Mediator-Design-Pattern.webp">

<p><strong>Key Characteristics of the Mediator Pattern</strong></p>
<ul>
    <li><strong>Decouples Components</strong>: Components do not need to know about each other's inner workings and can interact through the mediator.</li>
    <li><strong>Centralized Control</strong>: The mediator manages the communication between components, providing a single point of control.</li>
    <li><strong>Improved Maintainability</strong>: Changes to the interactions between components can often be made in the mediator without affecting the components themselves.</li>
</ul>

<p><strong>Why Use the Mediator Pattern?</strong></p>
<p>Use the Mediator Pattern when:</p>
<ul>
    <li>You want to reduce the dependencies between components that communicate with each other.</li>
    <li>You have a complex set of interactions that can be simplified by centralizing the control logic.</li>
    <li>You want to implement a communication protocol between multiple objects.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Consider an air traffic control system. The air traffic controller (the mediator) communicates with various aircraft (the components) to manage takeoffs, landings, and other instructions. The aircraft do not need to know about each other, only the controller, which directs their actions.</p>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Mediator Interface</strong>: Defines the interface for communication between components.</li>
    <li><strong>Concrete Mediator</strong>: Implements the mediator interface and coordinates communication between components.</li>
    <li><strong>Colleague Classes</strong>: Classes that communicate with each other through the mediator.</li>
</ol>

<p><strong>Steps to Implement the Mediator Pattern</strong></p>
<ol>
    <li>Create a <strong>Mediator Interface</strong> that defines methods for communication.</li>
    <li>Implement a <strong>Concrete Mediator</strong> that maintains references to the colleague objects and handles their interactions.</li>
    <li>Implement <strong>Colleague Classes</strong> that interact with the mediator instead of directly with each other.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example in Python demonstrating the Mediator Pattern with a chat room system:</p>

```python
class ChatMediator:
    def send_message(self, message, colleague):
        raise NotImplementedError

class ChatRoom(ChatMediator):
    def __init__(self):
        self.colleagues = []

    def register(self, colleague):
        self.colleagues.append(colleague)
        colleague.set_mediator(self)

    def send_message(self, message, colleague):
        for c in self.colleagues:
            if c != colleague:
                c.receive_message(message)

class Colleague:
    def __init__(self, name):
        self.name = name
        self.mediator = None

    def set_mediator(self, mediator):
        self.mediator = mediator

    def send_message(self, message):
        print(f"{self.name} sends: {message}")
        self.mediator.send_message(message, self)

    def receive_message(self, message):
        print(f"{self.name} received: {message}")

# Client Code
def main():
    chat_room = ChatRoom()

    alice = Colleague("Alice")
    bob = Colleague("Bob")
    charlie = Colleague("Charlie")

    chat_room.register(alice)
    chat_room.register(bob)
    chat_room.register(charlie)

    alice.send_message("Hello, everyone!")
    bob.send_message("Hi, Alice!")
    charlie.send_message("Hey there!")

if __name__ == "__main__":
    main()
```

<p><strong>Explanation:</strong></p>
<ul>
    <li>The <strong>ChatMediator</strong> interface defines the <code>send_message()</code> method for sending messages between colleagues.</li>
    <li>The <strong>ChatRoom</strong> class implements the mediator interface and manages the list of colleagues, sending messages to all except the sender.</li>
    <li>The <strong>Colleague</strong> class represents the participants in the chat room and has methods for sending and receiving messages.</li>
    <li>The <strong>Client Code</strong> demonstrates how to create a chat room, register colleagues, and facilitate communication through the mediator.</li>
</ul>

<p><strong>Output Example:</strong></p>
<pre><code>
Alice sends: Hello, everyone!
Bob received: Hello, everyone!
Charlie received: Hello, everyone!

Bob sends: Hi, Alice!
Alice received: Hi, Alice!
Charlie received: Hi, Alice!

Charlie sends: Hey there!
Alice received: Hey there!
Bob received: Hey there!
</code></pre>

<p>This example illustrates how the Mediator Pattern helps to centralize communication between components, reducing dependencies and promoting cleaner code. By using a mediator, changes to how components interact can be made without affecting the components themselves.</p>


<br>
<br>

<h2>Momento Design Pattern</h2>

<p>The Memento Pattern is a behavioral design pattern that allows an object to capture and store its internal state without exposing its implementation details. This pattern is particularly useful for implementing undo functionality in applications, as it enables an object to revert to a previous state when needed.</p>

<p><strong>Key Characteristics of the Memento Pattern</strong></p>
<ul>
    <li><strong>Encapsulates State</strong>: The internal state of an object is captured in a memento object, which can be stored and restored later.</li>
    <li><strong>Decouples Originator and Caretaker</strong>: The originator (the object whose state is being stored) does not need to know how the caretaker (the object managing the memento) handles the memento.</li>
    <li><strong>Supports Undo Functionality</strong>: Provides a mechanism to restore the previous state of an object, enabling undo operations.</li>
</ul>

<p><strong>Why Use the Memento Pattern?</strong></p>
<p>Use the Memento Pattern when:</p>
<ul>
    <li>You need to capture the internal state of an object at a specific point in time.</li>
    <li>You want to implement undo or rollback functionality without exposing the object's internal structure.</li>
    <li>You need to save and restore state without violating encapsulation.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Consider a text editor. As a user types, the editor can create snapshots (mementos) of the document's content. If the user wants to undo changes, the editor can restore the document to a previous snapshot, allowing the user to revert to earlier versions of the document without revealing the underlying implementation of how the document is stored.</p>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Memento</strong>: The object that stores the state of the originator.</li>
    <li><strong>Originator</strong>: The object whose state needs to be saved and restored.</li>
    <li><strong>Caretaker</strong>: The object that manages the mementos and handles the storage and retrieval of the memento.</li>
</ol>

<p><strong>Steps to Implement the Memento Pattern</strong></p>
<ol>
    <li>Create a <strong>Memento</strong> class that stores the state of the originator.</li>
    <li>Implement the <strong>Originator</strong> class that creates mementos and restores its state from them.</li>
    <li>Implement the <strong>Caretaker</strong> class that manages the mementos and interacts with the originator.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example in Python demonstrating the Memento Pattern with a simple text editor:</p>

```python
class Memento:
    def __init__(self, state):
        self.state = state

class TextEditor:
    def __init__(self):
        self.content = ""

    def set_content(self, content):
        self.content = content

    def create_memento(self):
        return Memento(self.content)

    def restore_from_memento(self, memento):
        self.content = memento.state

class Caretaker:
    def __init__(self):
        self.mementos = []

    def save_state(self, editor):
        self.mementos.append(editor.create_memento())

    def undo(self, editor):
        if self.mementos:
            last_memento = self.mementos.pop()
            editor.restore_from_memento(last_memento)

# Client Code
def main():
    editor = TextEditor()
    caretaker = Caretaker()

    editor.set_content("Version 1")
    caretaker.save_state(editor)

    editor.set_content("Version 2")
    caretaker.save_state(editor)

    editor.set_content("Version 3")

    print(f"Current Content: {editor.content}")  # Output: Current Content: Version 3

    caretaker.undo(editor)
    print(f"After Undo: {editor.content}")  # Output: After Undo: Version 2

    caretaker.undo(editor)
    print(f"After Undo: {editor.content}")  # Output: After Undo: Version 1

if __name__ == "__main__":
    main()
```

<p><strong>Explanation:</strong></p>
<ul>
    <li>The <strong>Memento</strong> class stores the state of the <strong>TextEditor</strong> (the content of the text).</li>
    <li>The <strong>TextEditor</strong> class is the originator that creates mementos and restores its content from them.</li>
    <li>The <strong>Caretaker</strong> class manages the history of mementos and provides functionality to save and restore states.</li>
    <li>The <strong>Client Code</strong> demonstrates how to use the caretaker to save and undo changes in the text editor.</li>
</ul>

<p><strong>Output Example:</strong></p>

```python
Current Content: Version 3
After Undo: Version 2
After Undo: Version 1
```

<p>This example illustrates how the Memento Pattern allows for capturing and restoring the state of an object while maintaining encapsulation, providing an elegant solution for implementing undo functionality in applications.</p>

<br>
<br>

<h2>Visitor Design Pattern</h2>

<p>The Visitor Pattern is a behavioral design pattern that allows you to separate an algorithm from the object structure on which it operates. This pattern enables you to add new operations to existing object structures without modifying those structures. It promotes the open/closed principle, which states that classes should be open for extension but closed for modification.</p>

<p><strong>Key Characteristics of the Visitor Pattern</strong></p>
<ul>
    <li><strong>Separation of Concerns</strong>: It separates the operation logic from the object structure, making it easier to manage and extend.</li>
    <li><strong>Extensibility</strong>: New operations can be added without modifying existing classes, promoting easier maintenance and flexibility.</li>
    <li><strong>Complexity Management</strong>: It can simplify complex object structures by encapsulating operations within visitor classes.</li>
</ul>

<p><strong>Why Use the Visitor Pattern?</strong></p>
<p>Use the Visitor Pattern when:</p>
<ul>
    <li>You need to perform operations on objects of different classes without modifying those classes.</li>
    <li>You want to define a new operation without changing the classes of the elements on which it operates.</li>
    <li>You have a complex object structure with many classes that need to be visited for operations.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Consider a shopping mall. Each store (element) offers different products (operations). A customer (visitor) can visit different stores to check out their products without altering the stores themselves. The stores can define how they want to present their products to customers without changing their internal structure.</p>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Visitor Interface</strong>: Declares a visit method for each type of element that can be visited.</li>
    <li><strong>Concrete Visitor</strong>: Implements the visitor interface to define specific operations for each element type.</li>
    <li><strong>Element Interface</strong>: Defines an accept method that takes a visitor as an argument.</li>
    <li><strong>Concrete Elements</strong>: Classes that implement the element interface and accept visitors.</li>
</ol>

<p><strong>Steps to Implement the Visitor Pattern</strong></p>
<ol>
    <li>Create a <strong>Visitor Interface</strong> that declares methods for visiting each type of element.</li>
    <li>Implement a <strong>Concrete Visitor</strong> that defines specific operations for each element type.</li>
    <li>Create an <strong>Element Interface</strong> with an accept method that accepts a visitor.</li>
    <li>Implement <strong>Concrete Elements</strong> that accept visitors and call the corresponding visit methods.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example in Python demonstrating the Visitor Pattern with a shopping cart system:</p>

```python
class ItemVisitor:
    def visit_book(self, book):
        pass

    def visit_electronics(self, electronics):
        pass

class Book:
    def __init__(self, title):
        self.title = title

    def accept(self, visitor):
        visitor.visit_book(self)

class Electronics:
    def __init__(self, name):
        self.name = name

    def accept(self, visitor):
        visitor.visit_electronics(self)

class ShoppingCartVisitor(ItemVisitor):
    def visit_book(self, book):
        print(f"Visiting book: {book.title}")

    def visit_electronics(self, electronics):
        print(f"Visiting electronics: {electronics.name}")

# Client Code
def main():
    book1 = Book("The Great Gatsby")
    book2 = Book("1984")
    electronics1 = Electronics("Laptop")
    electronics2 = Electronics("Smartphone")

    visitor = ShoppingCartVisitor()

    # Visiting items in the shopping cart
    items = [book1, book2, electronics1, electronics2]
    for item in items:
        item.accept(visitor)

if __name__ == "__main__":
    main()
```

<p><strong>Explanation:</strong></p>
<ul>
    <li>The <strong>ItemVisitor</strong> interface declares visit methods for different types of items (books and electronics).</li>
    <li>The <strong>Book</strong> and <strong>Electronics</strong> classes implement the <strong>accept()</strong> method, which calls the appropriate visit method of the visitor.</li>
    <li>The <strong>ShoppingCartVisitor</strong> class implements the <strong>ItemVisitor</strong> interface and defines specific operations for visiting books and electronics.</li>
    <li>The <strong>Client Code</strong> demonstrates how to create items and a visitor to visit those items.</li>
</ul>

<p><strong>Output Example:</strong></p>

```python
Visiting book: The Great Gatsby
Visiting book: 1984
Visiting electronics: Laptop
Visiting electronics: Smartphone
```

<p>This example illustrates how the Visitor Pattern allows operations to be added to an object structure without modifying the structure itself, promoting clean separation of concerns and enhancing maintainability. By using a visitor, we can easily extend functionality to new types of elements without altering their existing code.</p>

<br>
<br>

<h2>Proxy Design Pattern</h2>

<p>The Proxy Pattern is a structural design pattern that provides a surrogate or placeholder for another object to control access to it. The proxy acts as an intermediary, allowing you to manage interactions with the real object (the subject). This pattern is useful for scenarios like lazy initialization, access control, logging, or managing resource-intensive objects.</p>

<p><strong>Key Characteristics of the Proxy Pattern</strong></p>
<ul>
    <li><strong>Control Access</strong>: The proxy can manage access to the real object, providing additional functionality before or after delegating calls to the real object.</li>
    <li><strong>Lazy Initialization</strong>: The proxy can delay the creation or loading of the real object until it is actually needed.</li>
    <li><strong>Resource Management</strong>: It can help in managing resources, such as network connections, files, or other expensive operations.</li>
</ul>

<p><strong>Why Use the Proxy Pattern?</strong></p>
<p>Use the Proxy Pattern when:</p>
<ul>
    <li>You want to control access to an object that is expensive to create or manage.</li>
    <li>You need to add additional functionality (like logging or access control) without changing the original object.</li>
    <li>You want to create a placeholder for an object that may not exist yet or is not currently available.</li>
</ul>

<p><strong>Real-World Analogy</strong></p>
<p>Consider a real estate agent (the proxy) who represents a property owner (the real subject). The agent controls access to the property, showing it to potential buyers while managing appointments and inquiries. The buyers interact with the agent instead of directly with the property owner.</p>

<p><strong>Components Involved</strong></p>
<ol>
    <li><strong>Subject Interface</strong>: Defines the common interface for the real object and the proxy.</li>
    <li><strong>Real Subject</strong>: The actual object that the proxy represents.</li>
    <li><strong>Proxy</strong>: The proxy class that implements the subject interface and holds a reference to the real subject, controlling access to it.</li>
</ol>

<p><strong>Steps to Implement the Proxy Pattern</strong></p>
<ol>
    <li>Create a <strong>Subject Interface</strong> that defines the methods that can be called on the real subject.</li>
    <li>Implement the <strong>Real Subject</strong> class that contains the core functionality.</li>
    <li>Implement the <strong>Proxy</strong> class that also implements the subject interface and delegates calls to the real subject.</li>
</ol>

<p><strong>Python Example</strong></p>

<p>Here’s an example in Python demonstrating the Proxy Pattern with a simple image loading scenario:</p>

```python
class Image:
    def display(self):
        pass

class RealImage(Image):
    def __init__(self, filename):
        self.filename = filename
        self.load_image()

    def load_image(self):
        print(f"Loading image: {self.filename}")

    def display(self):
        print(f"Displaying image: {self.filename}")

class ProxyImage(Image):
    def __init__(self, filename):
        self.filename = filename
        self.real_image = None

    def display(self):
        if self.real_image is None:
            self.real_image = RealImage(self.filename)
        self.real_image.display()

# Client Code
def main():
    image1 = ProxyImage("photo1.jpg")
    image2 = ProxyImage("photo2.jpg")

    # The image is loaded only when it is displayed for the first time
    image1.display()  # Output: Loading image: photo1.jpg
                       #         Displaying image: photo1.jpg
    image1.display()  # Output: Displaying image: photo1.jpg
    image2.display()  # Output: Loading image: photo2.jpg
                       #         Displaying image: photo2.jpg

if __name__ == "__main__":
    main()
```

<p><strong>Explanation:</strong></p>
<ul>
    <li>The <strong>Image</strong> interface defines the <code>display()</code> method that both the real image and proxy implement.</li>
    <li>The <strong>RealImage</strong> class represents the actual image and contains the logic to load and display it.</li>
    <li>The <strong>ProxyImage</strong> class implements the proxy and controls access to the real image. It delays the loading of the real image until the display method is called for the first time.</li>
    <li>The <strong>Client Code</strong> demonstrates how to use the proxy to load and display images without directly interacting with the real image until necessary.</li>
</ul>

<p><strong>Output Example:</strong></p>

```python
Loading image: photo1.jpg
Displaying image: photo1.jpg
Displaying image: photo1.jpg
Loading image: photo2.jpg
Displaying image: photo2.jpg
```

<p>This example illustrates how the Proxy Pattern can provide a way to manage access to an object, delaying its initialization and adding extra functionality without modifying the original object. This approach enhances flexibility and can lead to improved performance in scenarios where resource management is essential.</p>
