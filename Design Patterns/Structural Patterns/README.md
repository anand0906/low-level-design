<h1>Structural Design Patterns</h1>
<p>Structural design pattern is a blueprint of how different objects and classes are combined together to form a bigger structure for achieving multiple goals altogether.</p>
<p>The patterns in structural designs show how unique pieces of a system can be combined together in an extensible and flexible manner. So, with the help structural design pattern we can target and change a specific parts of the structure without changing the entire structure.</p>
<ul>
	<li><strong>Extensibility : </strong>New parts can be added without needing to change the entire structure.</li>
	<li><strong>Reusability : </strong>Common components can be reused in different contexts, saving time and reducing complexity.</li>
	<li><strong>Flexibility : </strong>Changes to specific parts won’t disrupt the whole system; only the necessary component is adjusted.</li>
</ul>
<p>By using structural patterns, we create a well-organized, modular system. This approach allows us to modify, extend, or replace parts as needed without a major overhaul—perfect for evolving systems!</p>
<p><strong>Types of structural design patterns</strong></p>
<ul>
	<li><strong>Adapter</strong></li>
	<li><strong>Bridge</strong></li>
	<li><strong>Composite</strong></li>
	<li><strong>Decorator</strong></li>
	<li><strong>Fascade</strong></li>
	<li><strong>FlyWeight</strong></li>
	<li><strong>Proxy</strong></li>
</ul>

<br>
<br>

<h2>Adapter Design Pattern</h2>
<p>An Adapter Pattern says that just <strong>"converts the interface of a class into another interface that a client wants"</strong>.</p>
<p>In other words, to provide the interface according to client requirement while using the services of a class with a different interface.</p>
<p>The Adapter Pattern is also known as Wrapper.Since it is Wrapping the existing interface to new one based on cient requirements</p>
<p><strong>Adapter Design Pattern</strong> is a structural pattern that helps different classes or systems work together by acting as a bridge or “translator” between them. It allows incompatible interfaces to work together by “adapting” one class’s interface to match the interface expected by another.</p>

<p><strong>Advantages for Developers:</strong></p>
<ul>
    <li><strong>Reusability</strong>: Allows developers to use existing code with incompatible interfaces without modifying it.</li>
    <li><strong>Flexibility</strong>: Makes it easy to integrate new classes without rewriting them to fit existing structures.</li>
    <li><strong>Separation of Concerns</strong>: Keeps the codebase cleaner, with each component focusing on a single responsibility.</li>
</ul>

<p><strong>When to Use the Adapter Pattern:</strong></p>
<ul>
    <li>When you have incompatible interfaces but need them to work together.</li>
    <li>When you want to use a class that lacks the interface you need.</li>
    <li>When working with legacy systems where the code can’t be modified, but you need to integrate it with a new system.</li>
</ul>

<p><strong>Real-Time Analogy:</strong> Think of a <strong>power adapter</strong> for a laptop. When you travel to a country with different power outlets, you use a power adapter to connect your device to the power supply. The adapter “translates” the plug’s shape and voltage to be compatible with the new outlet, allowing your device to work seamlessly.</p>
<p>Another analogy for the <strong>Adapter Pattern</strong> is a <strong>language translator</strong>.</p>

<p><strong>Language Translator Analogy:</strong></p>
<p>Imagine two people who speak different languages (say, English and Spanish) want to communicate. They can’t understand each other directly, but a translator (adapter) can help. The translator listens to one person, translates their words, and then conveys the message to the other person in a language they understand. The translator effectively "adapts" one language to another, allowing communication between two otherwise incompatible parties.</p>

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240204210100/adapter-design-pattern.webp">

<p><strong>Key Points in the Analogy:</strong></p>
<ul>
    <li><strong>Two Incompatible Interfaces</strong>: The two people speak different languages.</li>
    <li><strong>The Adapter</strong>: The translator is the adapter, bridging the gap between the two languages.</li>
    <li><strong>Unified Communication</strong>: The translator enables communication without either person needing to learn the other language.</li>
</ul>

<p>In software terms, the adapter class enables objects with incompatible interfaces to interact, just like a translator allows people who speak different languages to communicate seamlessly.</p>

<p><strong>4. Real-Time Applications:</strong></p>
<ul>
    <li><strong>Payment Gateways</strong>: Adapting various payment systems to work within a single platform.</li>
    <li><strong>Data Conversion Tools</strong>: Converting file formats (e.g., PDF, Word, etc.) to be readable by different software.</li>
    <li><strong>Database Connectors</strong>: Making databases with different interfaces compatible with an application’s expected format.</li>
</ul>

<p><strong>Components of Adapter Design Pattern</strong></p>

<p>Below are the components of the adapter design pattern:</p>

<ul>
    <li><strong>Target Interface</strong>: Defines the interface expected by the client. It represents the set of operations that the client code can use. It’s the common interface that the client code interacts with.</li>
    <li><strong>Adaptee</strong>: The existing class or system with an incompatible interface that needs to be integrated into the new system. It’s the class or system that the client code cannot directly use due to interface mismatches.</li>
    <li><strong>Adapter</strong>: A class that implements the target interface and internally uses an instance of the adaptee to make it compatible with the target interface. It acts as a bridge, adapting the interface of the adaptee to match the target interface.</li>
    <li><strong>Client</strong>: The code that uses the target interface to interact with objects. It remains unaware of the specific implementation details of the adaptee and the adapter. It’s the code that benefits from the integration of the adaptee into the system through the adapter.</li>
</ul>

<p><strong>Different Implementations of Adapter Design Pattern</strong></p>

<p>The Adapter Design Pattern can be applied in various ways depending on the programming language and the specific context. Here are the primary implementations:</p>

<ol>
    <li><strong>Class Adapter (Inheritance-based)</strong></li>
    <p>In this approach, the adapter class inherits from both the target interface (the one the client expects) and the adaptee (the existing class needing adaptation). This approach is possible in languages that allow multiple inheritance, like C++.</p>
    <ul>
        <li><strong>Example</strong>: Imagine a media player that needs to play files in various formats. If a class adapter is used, it could inherit both the audio player and video player interfaces, adapting them to work under one interface.</li>
    </ul>
    <li><strong>Object Adapter (Composition-based)</strong></li>
    <p>Here, the adapter holds an instance of the adaptee instead of inheriting from it. The adapter implements the target interface and calls methods on the adaptee instance. This method is more flexible, as a single adapter can work with multiple adaptees.</p>
    <ul>
        <li><strong>Example</strong>: Imagine you have a payment processing app that supports various payment methods like PayPal and credit cards. Each payment method can be an object, and the object adapter can adapt any of them to a single, standard payment interface.</li>
    </ul>
    <li><strong>Two-way Adapter</strong></li>
    <p>A two-way adapter can act as both a target and an adaptee, depending on the interface being invoked. This is useful when two systems need to interact and require adaptation from both ends.</p>
    <ul>
        <li><strong>Example</strong>: Consider a system where an old printer and a new printer model need to work together. A two-way adapter would allow commands from either model to be adapted to the other, facilitating mutual compatibility.</li>
    </ul>
    <li><strong>Interface Adapter (Default Adapter)</strong></li>
    <p>If an interface contains many methods but only a few are needed, an interface adapter can provide default implementations for unused methods. This is helpful in languages like Java, where abstract classes allow only required methods to be implemented.</p>
    <ul>
        <li><strong>Example</strong>: In a GUI application, a listener interface might have multiple methods, such as onClick, onHover, onKeyPress, etc. If you only need to handle onClick, you can use an interface adapter to provide default implementations for the other methods.</li>
    </ul>
</ol>

<p><strong>How Adapter Design Pattern Works</strong></p>

<p>Below is how the adapter design pattern works:</p>

<ol>
    <li><strong>Step 1</strong>: The client initiates a request by calling a method on the adapter via the target interface.</li>
    <li><strong>Step 2</strong>: The adapter maps or transforms the client’s request into a format that the adaptee can understand using the adaptee’s interface.</li>
    <li><strong>Step 3</strong>: The adaptee does the actual job based on the translated request from the adapter.</li>
    <li><strong>Step 4</strong>: The client receives the results of the call, remaining unaware of the adapter’s presence or the specific details of the adaptee.</li>
</ol>

<p><strong>Examples For Class Adpater : </strong></p>
<p>Suppose we have an AudioPlayer that can only play MP3 files, and we want it to also play MP4 files by adapting it.</p>

```python
# Target Interface: The client expects this interface to work with.
from abc import ABC, abstractmethod

class MediaPlayer(ABC):

	@abstractmethods
    def play(self, filename):
        pass

# Adaptee: Existing class with incompatible interface
class MP4Player:
    def play_mp4(self, filename):
        print(f"Playing MP4 file: {filename}")

# Adapter: Inherits from both the target and adaptee, adapting MP4Player to MediaPlayer
class AudioPlayer(MediaPlayer, MP4Player):
    def play(self, filename):
        if filename.endswith(".mp4"):
            self.play_mp4(filename)  # Adapts the MP4 method to work with MediaPlayer
        else:
            print(f"Cannot play {filename}: Unsupported format")

# Client code
player = AudioPlayer()
player.play("video.mp4")     # Output: Playing MP4 file: video.mp4
player.play("song.mp3")      # Output: Cannot play song.mp3: Unsupported format
```

<p><strong>Explanation : </strong></p>
<ol>
	<li><strong>MediaPlayer :</strong>The target interface expected by the client.</li>
	<li><strong>Mp4Player :</strong>The adaptee class with a different interface (play_mp4 method).</li>
	<li><strong>AudioPlayer(Adapter) :</strong>The class adapter that inherits both MediaPlayer and MP4Player and adapts MP4Player to the MediaPlayer interface by implementing play and calling play_mp4 when appropriate.</li>
</ol>
<p>Here, the AudioPlayer (adapter) bridges the gap by allowing MP4Player to fit into the MediaPlayer interface, enabling the client to use it transparently.</p>

<p><strong>Example For Object Adpater :</strong></p>
<p>An Object Adapter uses composition instead of inheritance to adapt one interface to another. In this case, the adapter holds an instance of the adaptee and delegates the calls to it. This allows for more flexibility, as the adapter can work with different adaptees without needing to modify the adapter itself.</p>

<p>Let's extend the previous example, where we want our MediaPlayer to be able to play both MP3 and MP4 files. We will create an object adapter to adapt the MP4Player to our MediaPlayer interface.</p>

```python
# Target Interface: The client expects this interface to work with.
from abc import ABC, abstractmethod

class MediaPlayer(ABC):

	@abstractmethod
    def play(self, filename):
        pass

# Adaptee: Existing class with incompatible interface
class MP4Player:
    def play_mp4(self, filename):
        print(f"Playing MP4 file: {filename}")

# Adapter: Uses composition to hold an instance of the adaptee
class MediaAdapter(MediaPlayer):
    def __init__(self, adaptee):
        self.adaptee = adaptee
    
    def play(self, filename):
        if filename.endswith(".mp4"):
            self.adaptee.play_mp4(filename)  # Delegate to adaptee's method
        else:
            print(f"Cannot play {filename}: Unsupported format")

# Client code
class AudioPlayer(MediaPlayer):
    def __init__(self):
        self.media_adapter = MediaAdapter(MP4Player())  # Create adapter with adaptee

    def play(self, filename):
        if filename.endswith(".mp3"):
            print(f"Playing MP3 file: {filename}")  # Handle MP3 directly
        else:
            self.media_adapter.play(filename)  # Delegate to the adapter for other formats

# Using the client
player = AudioPlayer()
player.play("song.mp3")     # Output: Playing MP3 file: song.mp3
player.play("video.mp4")    # Output: Playing MP4 file: video.mp4
player.play("audio.wav")    # Output: Cannot play audio.wav: Unsupported format
```

<p><strong>Explanation:</strong></p>
<ul>
    <li><strong>MediaPlayer</strong>: The target interface that the client expects.</li>
    <li><strong>MP4Player</strong>: The adaptee class that can play MP4 files but doesn’t conform to the MediaPlayer interface.</li>
    <li><strong>MediaAdapter</strong>: The object adapter that holds an instance of MP4Player and implements the MediaPlayer interface. It translates calls to play into calls to the appropriate method of MP4Player.</li>
    <li><strong>AudioPlayer</strong>: The client class that uses the MediaAdapter to play different media formats.</li>
</ul>

<p><strong>Key Points:</strong></p>
<ul>
    <li>The Object Adapter pattern allows the adapter to be flexible. You can easily change the adaptee that the adapter is using without modifying the adapter itself.</li>
    <li>This implementation can easily adapt multiple different classes by creating additional adapters if needed, promoting code reusability.</li>
</ul>

<p><strong>Example For Two Way Adapter : </strong></p>

```python
# Target Interface: The client expects this interface to work with.
from abc import ABC, abstractmethod
class VideoPlayer(ABC):

	@abstractmethod
    def play(self, video_id):
        pass
    
    @abstractmethod
    def pause(self):
        pass
    
    @abstractmethod
    def get_status(self):
        pass

# Adaptee: The existing class with an incompatible interface
class StreamingService:
    def start_video(self, video_id):
        print(f"Starting video with ID: {video_id}")
    
    def stop_video(self):
        print("Stopping video.")
    
    def is_video_playing(self):
        return True  # Assume video is always playing for this example

# Two-way Adapter: Acts as both the video player and the streaming service
class VideoAdapter(VideoPlayer):
    def __init__(self, service):
        self.service = service
        self.current_video_id = None
    
    def play(self, video_id):
        self.current_video_id = video_id
        self.service.start_video(video_id)  # Delegate to the service

    def pause(self):
        self.service.stop_video()  # Delegate to the service

    def get_status(self):
        if self.service.is_video_playing():
            return f"Video {self.current_video_id} is currently playing."
        else:
            return "No video is currently playing."

# Client code
streaming_service = StreamingService()
adapter = VideoAdapter(streaming_service)

# Client can start playing a video
adapter.play("12345")  # Output: Starting video with ID: 12345

# Client can get the status of the video
print(adapter.get_status())  # Output: Video 12345 is currently playing.

# Client can pause the video
adapter.pause()  # Output: Stopping video.

# Check status after pausing
print(adapter.get_status())  # Output: Video 12345 is currently playing.
```

<p><strong>Classes:</strong></p>
<ul>
    <li><strong>VideoPlayer</strong>: The target interface that the client expects to work with.</li>
    <li><strong>StreamingService</strong>: The adaptee class with methods for starting, stopping, and checking the status of videos, but doesn’t conform to the VideoPlayer interface.</li>
    <li><strong>VideoAdapter</strong>: The two-way adapter that implements the VideoPlayer interface. It holds an instance of StreamingService and translates calls to its methods into corresponding calls on the service.</li>
</ul>

<p><strong>Client code:</strong></p>
<ol>
    <li>The client can start playing a video by calling <code>adapter.play("12345")</code>, which outputs: <em>Starting video with ID: 12345</em>.</li>
    <li>The client can check the status of the video by calling <code>adapter.get_status()</code>, which outputs: <em>Video 12345 is currently playing.</em>.</li>
    <li>The client can pause the video by calling <code>adapter.pause()</code>, which outputs: <em>Stopping video.</em>.</li>
    <li>After pausing, the client can check the status again, which outputs: <em>Video 12345 is currently playing.</em>.</li>
</ol>

<p><strong>Key Points:</strong></p>
<ul>
    <li>This two-way adapter facilitates smooth communication between the VideoPlayer interface and the StreamingService, allowing for both playback and feedback.</li>
    <li>The two-way adapter pattern is beneficial for scenarios where two systems need to interact with each other bi-directionally, enhancing the integration of components in a system.</li>
</ul>

<p><strong>Examples for Interface adapter</strong></p>
<p>In this example, we will create a general <strong>Student</strong> interface that has several methods. However, not all methods will be relevant for both types of students, so we'll use an interface adapter to simplify the implementation.</p>


```python
# Target Interface: General Student interface with several methods
class Student:
    def study(self):
        pass
    
    def take_exam(self):
        pass
    
    def attend_class(self):
        pass
    
    def graduate(self):
        pass

# Interface Adapter: Provides default implementations for unused methods
class StudentAdapter(Student):
    def graduate(self):
        pass  # Not applicable for SchoolStudent

# Concrete Class: SchoolStudent uses the StudentAdapter to implement only needed methods
class SchoolStudent(StudentAdapter):
    def study(self):
        print("School student studying for exams.")
    
    def take_exam(self):
        print("School student taking a standardized test.")
    
    def attend_class(self):
        print("School student attending classes.")

# Concrete Class: CollegeStudent implements all methods from Student
class CollegeStudent(Student):
    def study(self):
        print("College student studying for finals.")
    
    def take_exam(self):
        print("College student taking a midterm exam.")
    
    def attend_class(self):
        print("College student attending lectures.")
    
    def graduate(self):
        print("College student graduating with a degree.")

# Client code
school_student = SchoolStudent()
school_student.study()        # Output: School student studying for exams.
school_student.take_exam()    # Output: School student taking a standardized test.
school_student.attend_class()  # Output: School student attending classes.
# school_student.graduate()   # This would not be applicable, so no implementation

college_student = CollegeStudent()
college_student.study()        # Output: College student studying for finals.
college_student.take_exam()    # Output: College student taking a midterm exam.
college_student.attend_class()  # Output: College student attending lectures.
college_student.graduate()      # Output: College student graduating with a degree.
```


<p><strong>Classes:</strong></p>
<ul>
    <li><strong>Student</strong>: The target interface defining several methods relevant to all types of students.</li>
    <li><strong>StudentAdapter</strong>: The interface adapter that provides a default implementation for the <code>graduate</code> method, which is not applicable for <strong>SchoolStudent</strong>.</li>
    <li><strong>SchoolStudent</strong>: The concrete class that extends <strong>StudentAdapter</strong>. It implements only the <code>study</code>, <code>take_exam</code>, and <code>attend_class</code> methods, while the <code>graduate</code> method is inherited with a default implementation.</li>
    <li><strong>CollegeStudent</strong>: The concrete class that implements the full <strong>Student</strong> interface, providing implementations for all methods, including <code>graduate</code>.</li>
</ul>

<p><strong>Client Code:</strong></p>
<ol>
    <li>The client creates an instance of <strong>SchoolStudent</strong> and calls the relevant methods:
        <ul>
            <li><code>school_student.study()</code> outputs: <em>School student studying for exams.</em></li>
            <li><code>school_student.take_exam()</code> outputs: <em>School student taking a standardized test.</em></li>
            <li><code>school_student.attend_class()</code> outputs: <em>School student attending classes.</em></li>
        </ul>
    </li>
    <li>The client creates an instance of <strong>CollegeStudent</strong> and calls all methods:
        <ul>
            <li><code>college_student.study()</code> outputs: <em>College student studying for finals.</em></li>
            <li><code>college_student.take_exam()</code> outputs: <em>College student taking a midterm exam.</em></li>
            <li><code>college_student.attend_class()</code> outputs: <em>College student attending lectures.</em></li>
            <li><code>college_student.graduate()</code> outputs: <em>College student graduating with a degree.</em></li>
        </ul>
    </li>
</ol>

<p><strong>Key Points:</strong></p>
<ul>
    <li>The <strong>Interface Adapter</strong> pattern allows <strong>SchoolStudent</strong> to inherit unnecessary methods without implementing them, leading to cleaner and more focused code.</li>
    <li>This pattern is useful in situations where certain methods are not applicable for all subclasses, thus promoting flexibility and maintainability.</li>
</ul>


<br>
<br>

<h2>Facade Design Pattern</h2>
<p><strong>Facade Design Pattern</strong> is a structural pattern that provides a simple, unified interface to a complex system of classes or subsystems. Think of it like a “front desk” that handles customer requests instead of making you navigate through the complex workings behind the scenes. The Facade acts as a “single point of contact” to make things easier to use, hiding the complexity from the client.</p>

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240118172253/facade-method-banner.jpg">
<img src="https://www.tutorialspoint.com/design_pattern/images/facade_pattern_uml_diagram.jpg">

<p><strong>Key Aspects of the Facade Pattern</strong></p>
<ul>
    <li><strong>Simplifies Complex Systems</strong>: It hides the detailed operations of multiple classes, providing a straightforward interface for the end user.</li>
    <li><strong>Makes Code More Modular</strong>: Developers can work with one simple interface rather than needing to understand or modify multiple classes directly.</li>
</ul>

<p><strong>Advantages for Developers</strong></p>
<ul>
    <li><strong>Reduces Complexity</strong>: Facade simplifies interactions with a complex subsystem, making the code easier to use and understand.</li>
    <li><strong>Decouples the Code</strong>: Allows developers to change underlying classes without affecting other parts of the program, as the client only interacts with the facade.</li>
    <li><strong>Improves Code Organization</strong>: By reducing the direct interdependencies between classes, the Facade pattern makes the code more organized and maintainable.</li>
</ul>

<p><strong>When to Use the Facade Pattern</strong></p>
<ol>
    <li><strong>To Hide Complexity</strong>: When you have a complex system with many interdependent classes and you want to provide a simpler interface.</li>
    <li><strong>To Make Code More Manageable</strong>: When you want to keep the code organized by reducing dependencies.</li>
    <li><strong>When Upgrading or Expanding Systems</strong>: It’s useful when you’re expanding or upgrading a system, as you can make changes behind the facade without impacting the client.</li>
</ol>

<p><strong>Real-World Analogy</strong></p>
<p>Think of a <strong>hotel reception desk</strong> as a Facade:</p>
<ul>
    <li>At the reception, you can check in, check out, order room service, or book a cab. You don’t have to interact directly with housekeeping, the kitchen, or the transportation department. The front desk simplifies your interaction with the hotel by handling all these complex interactions for you.</li>
</ul>

<p><strong>Real-World Applications</strong></p>
<ul>
    <li><strong>Libraries</strong>: Facades are commonly used in complex libraries or frameworks, where a single, user-friendly API interacts with various underlying classes and services.</li>
    <li><strong>Media Players</strong>: Media players use facades to allow users to play, pause, and stop a video without knowing the technical details of video processing.</li>
    <li><strong>Banking Applications</strong>: In online banking apps, users can manage accounts, transfer funds, and pay bills through a unified interface, which hides all the backend complexity.</li>
</ul>

<p><strong>Steps to Implement the Facade Pattern</strong></p>
<ol>
    <li><strong>Identify the Complex Subsystem</strong>: Choose the classes or subsystems that perform the intricate operations.</li>
    <li><strong>Create a Facade Class</strong>: Design a single class that will provide simple methods for the client to access.</li>
    <li><strong>Delegate Calls to Subsystems</strong>: The facade class should delegate tasks to the respective classes within the subsystem.</li>
    <li><strong>Use the Facade in Your Code</strong>: Instead of interacting with individual subsystem classes, the client should use the facade.</li>
</ol>

<p><strong>Examples Using Python</strong></p>

<p><strong>1. Basic Example: Car Start System</strong></p>

```python
# Complex subsystems
class Engine:
    def start(self):
        print("Engine started.")

class FuelPump:
    def pump(self):
        print("Fuel pump activated.")

class Battery:
    def provide_power(self):
        print("Battery providing power.")

# Facade
class CarFacade:
    def __init__(self):
        self.engine = Engine()
        self.fuel_pump = FuelPump()
        self.battery = Battery()

    def start_car(self):
        self.battery.provide_power()
        self.fuel_pump.pump()
        self.engine.start()

# Client code
car = CarFacade()
car.start_car()
```
<p>Here, CarFacade simplifies the process of starting the car by providing a start_car method that handles all the details internally.</p>

<p><strong>2. Example: Home Theater System</strong></p>

```python
# Complex subsystems
class Amplifier:
    def on(self): print("Amplifier on.")
    def set_volume(self, level): print(f"Amplifier volume set to {level}")

class DVDPlayer:
    def on(self): print("DVD Player on.")
    def play(self, movie): print(f"Playing '{movie}'")

class Projector:
    def on(self): print("Projector on.")
    def wide_screen_mode(self): print("Projector in widescreen mode.")

# Facade
class HomeTheaterFacade:
    def __init__(self, amp, dvd, projector):
        self.amp = amp
        self.dvd = dvd
        self.projector = projector

    def watch_movie(self, movie):
        print("Get ready to watch a movie...")
        self.amp.on()
        self.amp.set_volume(5)
        self.dvd.on()
        self.dvd.play(movie)
        self.projector.on()
        self.projector.wide_screen_mode()

# Client code
amp = Amplifier()
dvd = DVDPlayer()
projector = Projector()
home_theater = HomeTheaterFacade(amp, dvd, projector)

home_theater.watch_movie("Inception")

```

<p>In this example, the HomeTheaterFacade simplifies the process of setting up the home theater system, allowing the user to call a single watch_movie method.</p>

<br>
<br>

<h2>Decorator Design Pattern</h2>
<p><strong>Decorator Design Pattern</strong> is a structural pattern used to add behavior or responsibilities to objects dynamically. Unlike subclassing, which adds functionality at compile time, decorators are applied at runtime, allowing you to add or modify functionality without altering the existing codebase.</p>

<p><strong>Key Aspects of the Decorator Pattern</strong></p>
<ul>
    <li><strong>Dynamic Behavior Addition</strong>: The pattern allows new responsibilities to be added to objects without modifying their structure or requiring subclassing.</li>
    <li><strong>Flexible and Scalable</strong>: It provides flexibility by allowing combinations of decorators, making it easy to mix and match features.</li>
</ul>

<p><strong>Advantages for Developers</strong></p>
<ul>
    <li><strong>Extensibility</strong>: Decorators enable functionality to be added or extended at runtime, making it easy to adapt as requirements change.</li>
    <li><strong>Separation of Concerns</strong>: Each decorator focuses on a specific responsibility, promoting modularity and reusability.</li>
    <li><strong>Avoids Class Explosion</strong>: Instead of creating multiple subclasses for various combinations of behaviors, decorators allow you to stack functionality as needed.</li>
</ul>

<p><strong>When to Use the Decorator Pattern</strong></p>
<ol>
    <li><strong>To Add Behavior Dynamically</strong>: When you need to add responsibilities to objects at runtime.</li>
    <li><strong>When Subclassing Isn’t Practical</strong>: When subclassing would result in a large number of subclasses to cover all possible combinations.</li>
    <li><strong>When Core Functionality Should Remain Unchanged</strong>: The base object remains unchanged, but its behavior can be altered using decorators.</li>
</ol>

<p><strong>Real-World Analogy</strong></p>
<p>Consider a <strong>coffee shop</strong> where you can customize a basic coffee with options like milk, sugar, or flavors. Starting with a basic coffee, you can add any number of additional toppings to it without changing the original coffee itself.</p>

<p><strong>Real-World Applications</strong></p>
<ul>
    <li><strong>User Interfaces</strong>: Adding scrollbars to text fields, borders to windows, or toolbars to applications without altering the original UI component classes.</li>
    <li><strong>Logging</strong>: Adding logging, security, or notification functionality dynamically to classes.</li>
    <li><strong>Data Processing</strong>: Wrapping data in various decorators to apply filters, formatters, or transformations.</li>
</ul>

<p><strong>Steps to Implement the Decorator Pattern</strong></p>
<ol>
    <li><strong>Create a Base Interface or Abstract Class</strong>: This represents the core object to be decorated.</li>
    <li><strong>Implement the Core Component</strong>: This is the primary implementation of the base class or interface.</li>
    <li><strong>Create a Decorator Class</strong>: This class should also inherit from the base type and include a reference to the object it decorates.</li>
    <li><strong>Add Decorator Subclasses for Each Behavior</strong>: Each subclass of the decorator adds specific behavior, forwarding requests to the decorated object.</li>
    <li><strong>Apply Decorators as Needed</strong>: Use multiple decorators by wrapping them around the core object as needed.</li>
</ol>

<p><strong>Example Using Python</strong></p>

<p><strong>1. Coffee Shop Example</strong></p>

```python
from abc import ABC, abstractmethod

# Component Interface
class Coffee(ABC):
    @abstractmethod
    def cost(self):
        pass

# Concrete Component
class BasicCoffee(Coffee):
    def cost(self):
        return 5

# Decorator Base Class
class CoffeeDecorator(Coffee):
    def __init__(self, coffee):
        self._coffee = coffee

    def cost(self):
        return self._coffee.cost()

# Concrete Decorators
class MilkDecorator(CoffeeDecorator):
    def cost(self):
        return self._coffee.cost() + 2  # Adding milk cost

class SugarDecorator(CoffeeDecorator):
    def cost(self):
        return self._coffee.cost() + 1  # Adding sugar cost

# Client Code
coffee = BasicCoffee()
coffee_with_milk = MilkDecorator(coffee)
coffee_with_milk_and_sugar = SugarDecorator(coffee_with_milk)

print("Cost of coffee with milk and sugar:", coffee_with_milk_and_sugar.cost())  # Output: 8

```

<p>In this example, BasicCoffee is the core coffee. We add milk and sugar decorators to increase the cost dynamically.</p>

<p><strong>2. Text Processing Example</strong></p>

```python
from abc import ABC, abstractmethod
# Component Interface
class Text(ABC):
    @abstractmethod
    def format(self, text):
        pass

# Concrete Component
class PlainText(Text):
    def format(self, text):
        return text

# Decorator Base Class
class TextDecorator(Text):
    def __init__(self, text):
        self._text = text

    def format(self, text):
        return self._text.format(text)

# Concrete Decorators
class BoldDecorator(TextDecorator):
    def format(self, text):
        return f"<b>{self._text.format(text)}</b>"

class ItalicDecorator(TextDecorator):
    def format(self, text):
        return f"<i>{self._text.format(text)}</i>"

# Client Code
text = PlainText()
bold_text = BoldDecorator(text)
italic_bold_text = ItalicDecorator(bold_text)

print(italic_bold_text.format("Hello, World!"))  # Output: <i><b>Hello, World!</b></i>
```
<p>Here, we dynamically wrap PlainText with bold and italic decorators to format text as < i > < b >Hello, World!< /b >< /i > without modifying the original PlainText class.</p>

<br>
<br>

<h2>Composite Design Pattern</h2>
<p><strong>Composite Design Pattern in Simple Words</strong></p>
<p>The <strong>Composite Design Pattern</strong> is a structural pattern that lets you group objects into tree-like structures to represent part-whole hierarchies. It allows you to treat individual objects and groups of objects in the same way, making it easier to work with complex structures that contain many small objects.</p>
<p>In other words, with the composite pattern, you can represent both simple and complex objects uniformly. You can create complex objects by combining simple objects in a structured way, and interact with these complex objects as if they were simple.</p>

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240213162314/composite-design-pattern-iin-java.webp">

<p><strong>Advantages for Developers</strong></p>
<ul>
  <li><strong>Simplifies Complex Structures</strong>: Composite design pattern allows you to build complex structures in a simple, organized way, making it easier to understand and work with.</li>
  <li><strong>Uniformity</strong>: Treats individual objects and composite structures the same way, which helps in keeping the code base clean and reduces the number of conditional checks.</li>
  <li><strong>Scalability</strong>: Makes it easy to add new types of components without altering existing code, enhancing the code's flexibility and scalability.</li>
  <li><strong>Encapsulates Object Hierarchies</strong>: By encapsulating the structure, it allows developers to build flexible systems that manage objects hierarchically.</li>
</ul>

<p><strong>When to Use the Composite Pattern</strong></p>
<ul>
  <li>You need to represent a <strong>hierarchical structure</strong> of objects, like a tree structure.</li>
  <li>You want clients to <strong>treat individual objects and groups of objects uniformly</strong>.</li>
  <li>You want to manage complex structures that involve multiple small objects.</li>
</ul>

<p><strong>Real-Time Analogy</strong></p>
<p>Imagine a <strong>file system</strong> on your computer. You have files and folders:</p>
<ul>
  <li>Each file is an individual item.</li>
  <li>Each folder can contain files and other folders.</li>
</ul>
<p>In this system:</p>
<ul>
  <li>You can treat files and folders the same way (e.g., get size, delete).</li>
  <li>Folders can contain a mix of files and other folders, just like composite structures can contain individual objects and other composite objects.</li>
</ul>

<p><strong>Real-Time Applications of Composite Pattern</strong></p>
<ul>
  <li><strong>Graphical User Interfaces (GUIs)</strong>: GUIs often use composite patterns for representing windows, panels, and individual components (buttons, text boxes, etc.).</li>
  <li><strong>Document Structures</strong>: Complex documents that contain text, images, tables, etc., use the composite pattern to allow each element to be treated uniformly.</li>
  <li><strong>File System Management</strong>: As described in the analogy, file systems can use composite patterns to handle files and directories hierarchically.</li>
</ul>

<img src="https://images.javatpoint.com/images/designpattern/compositeuml1.jpg">

<p><strong>Components Involved in the Composite Pattern</strong></p>
<ol>
  <li><strong>Component</strong>: Defines the common interface for all objects in the hierarchy. Both simple (leaf) and composite (container) objects implement this interface.</li>
  <li><strong>Leaf</strong>: Represents the individual objects in the hierarchy, which do not contain other objects.</li>
  <li><strong>Composite</strong>: A composite object can contain other components, including other composites, allowing it to create complex structures.</li>
</ol>

<p><strong>Steps to Implement the Composite Pattern</strong></p>
<ol>
  <li><strong>Define a Component Interface</strong> that declares common methods for both leaf and composite objects.</li>
  <li><strong>Create Leaf Classes</strong> that implement the Component interface and represent individual objects.</li>
  <li><strong>Create Composite Classes</strong> that implement the Component interface and contain methods to add, remove, and manage child components.</li>
  <li><strong>Client Code</strong> interacts with objects using the Component interface, allowing it to work with leaf and composite objects uniformly.</li>
</ol>

<p><strong>Example of Composite Pattern in Python</strong></p>

```python
from abc import ABC, abstractmethod

# Component Interface
class FileSystemComponent(ABC):
    @abstractmethod
    def show_details(self, indent=0):
        pass

# Leaf
class File(FileSystemComponent):
    def __init__(self, name):
        self.name = name

    def show_details(self, indent=0):
        print(" " * indent + self.name)

# Composite
class Folder(FileSystemComponent):
    def __init__(self, name):
        self.name = name
        self.children = []

    def add(self, component):
        self.children.append(component)

    def remove(self, component):
        self.children.remove(component)

    def show_details(self, indent=0):
        print(" " * indent + self.name + "/")
        for child in self.children:
            child.show_details(indent + 2)

# Client code
if __name__ == "__main__":
    # Create leaf objects
    file1 = File("file1.txt")
    file2 = File("file2.txt")
    file3 = File("file3.jpg")

    # Create composite objects (folders)
    folder1 = Folder("Documents")
    folder2 = Folder("Pictures")

    # Add files to folders
    folder1.add(file1)
    folder1.add(file2)
    folder2.add(file3)

    # Create root folder and add subfolders
    root = Folder("Root")
    root.add(folder1)
    root.add(folder2)

    # Show the entire structure
    root.show_details()
```

<p><strong>Example Output</strong></p>
<pre><code>Root/
  Documents/
    file1.txt
    file2.txt
  Pictures/
    file3.jpg</code></pre>

<p><strong>Explanation of Python Example</strong></p>
<ol>
  <li><strong>FileSystemComponent</strong>: This is an abstract base class (interface) that defines a <code>show_details</code> method, which will be implemented by both files and folders.</li>
  <li><strong>File</strong>: A leaf class representing individual files. Implements <code>show_details</code> to print the file name.</li>
  <li><strong>Folder</strong>: A composite class representing folders, which can contain files and other folders. Implements <code>show_details</code> to print its contents.</li>
  <li><strong>Client Code</strong>: Demonstrates creating a structure of folders and files and displays their hierarchy.</li>
</ol>

<p><strong>More Examples Using Python</strong></p>
<ul>
  <li><strong>Company Hierarchy</strong>: Composite pattern can represent employees (individual objects) and departments (composites of employees).</li>
  <li><strong>Menu System in Restaurants</strong>: Represents individual items as leaves and different categories (like drinks, main course, dessert) as composites.</li>
</ul>

<p>By applying the Composite Pattern, you can structure complex hierarchies while keeping the implementation flexible and the client code simple, as it interacts with all components through a single interface.</p>


<br>
<br>


<h2>Bridge Design Pattern</h2>
<p><strong>Bridge Design Pattern in Simple Words</strong></p>
<p>The <strong>Bridge Design Pattern</strong> is a structural pattern that separates an object’s abstraction (what it does) from its implementation (how it does it) so that the two can vary independently. This is especially helpful when you have multiple types of objects that need different implementations for each type, and you want to manage this complexity.</p>
<p>In simpler terms, the Bridge Pattern provides flexibility by “bridging” an interface with its implementation, allowing both to be extended without impacting each other. Think of it as creating two parts that work together without being tightly bound.</p>

<p><strong>Advantages for Developers</strong></p>
<ul>
  <li><strong>Improved Code Organization</strong>: Separates high-level logic from implementation details, making the code more modular and manageable.</li>
  <li><strong>Enhanced Flexibility</strong>: Allows abstraction and implementation to evolve independently, meaning new abstractions or implementations can be added without affecting the existing code.</li>
  <li><strong>Simplifies Complex Systems</strong>: Makes complex structures easier to understand, manage, and extend by decoupling classes.</li>
  <li><strong>Reduces Code Duplication</strong>: Avoids code redundancy by reusing implementations across different abstractions.</li>
</ul>

<p><strong>When to Use the Bridge Pattern</strong></p>
<ul>
  <li>You have a growing number of classes due to a mix of multiple types of abstractions and implementations, and you want to reduce the complexity.</li>
  <li>You want to keep the abstraction and implementation loosely coupled.</li>
  <li>You need to be able to change either the abstraction or the implementation independently.</li>
</ul>

<p><strong>Real-Time Analogy</strong></p>
<p>Imagine you are creating a <strong>remote control for devices</strong>:</p>
<ul>
  <li>A remote control can control different devices (TV, AC, fan), so it serves as the “abstraction.”</li>
  <li>Each device can have various actions (turn on, turn off, adjust settings), which are “implementations.”</li>
</ul>
<p>In this analogy, the Bridge Pattern allows you to extend the types of devices and remote functionalities independently without modifying the existing code for other devices or remotes.</p>

<p><strong>Real-Time Applications of Bridge Pattern</strong></p>
<ul>
  <li><strong>Cross-Platform GUIs</strong>: Allows an interface (e.g., buttons, windows) to work across multiple platforms (Windows, macOS, Linux).</li>
  <li><strong>Database Drivers</strong>: Enables a database interface to interact with different databases (MySQL, MongoDB, SQLite) without changing how the interface works.</li>
  <li><strong>Payment Systems</strong>: For applications needing to process payments with various providers (PayPal, Stripe), where each provider has its own implementation.</li>
</ul>

<p><strong>Components Involved in the Bridge Pattern</strong></p>
<ol>
  <li><strong>Abstraction</strong>: Defines the high-level control and delegates implementation-specific work to the implementer.</li>
  <li><strong>Refined Abstraction</strong>: Extends the abstraction, adding more high-level functionality.</li>
  <li><strong>Implementer</strong>: An interface or abstract class that defines operations to be implemented by concrete implementations.</li>
  <li><strong>Concrete Implementer</strong>: Provides the actual implementation of the operations defined in the implementer.</li>
</ol>

<p><strong>Steps to Implement the Bridge Pattern</strong></p>
<ol>
  <li><strong>Define the Abstraction Interface</strong> that represents the main control logic.</li>
  <li><strong>Create Implementer Interface</strong> to declare specific methods required by implementations.</li>
  <li><strong>Develop Concrete Implementers</strong> that implement the Implementer interface.</li>
  <li><strong>Implement Refined Abstraction</strong> if any specific behavior or higher-level functionality is needed.</li>
  <li><strong>Client Code</strong> interacts with the abstraction interface, which delegates work to the implementer.</li>
</ol>

<p><strong>Example of Bridge Pattern in Python</strong></p>

```python

from abc import ABC, abstractmethod

# Implementer
class Device(ABC):
    @abstractmethod
    def turn_on(self):
        pass

    @abstractmethod
    def turn_off(self):
        pass

# Concrete Implementer
class TV(Device):
    def turn_on(self):
        print("TV is now ON")

    def turn_off(self):
        print("TV is now OFF")

class Radio(Device):
    def turn_on(self):
        print("Radio is now ON")

    def turn_off(self):
        print("Radio is now OFF")

# Abstraction
class RemoteControl:
    def __init__(self, device: Device):
        self.device = device

    def turn_on(self):
        self.device.turn_on()

    def turn_off(self):
        self.device.turn_off()

# Refined Abstraction
class AdvancedRemoteControl(RemoteControl):
    def mute(self):
        print("Device is now muted")

# Client Code
if __name__ == "__main__":
    tv = TV()
    radio = Radio()

    remote = RemoteControl(tv)
    remote.turn_on()
    remote.turn_off()

    advanced_remote = AdvancedRemoteControl(radio)
    advanced_remote.turn_on()
    advanced_remote.mute()
    advanced_remote.turn_off()
```

<p><strong>Example Output</strong></p>
<pre><code>TV is now ON
TV is now OFF
Radio is now ON
Device is now muted
Radio is now OFF</code></pre>

<p><strong>Explanation of Python Example</strong></p>
<ol>
  <li><strong>Device</strong>: The <code>Device</code> class is the implementer interface defining <code>turn_on</code> and <code>turn_off</code> methods, which concrete devices (like TV and Radio) must implement.</li>
  <li><strong>TV and Radio</strong>: These are concrete implementers providing specific implementations for <code>turn_on</code> and <code>turn_off</code>.</li>
  <li><strong>RemoteControl</strong>: Acts as the abstraction, controlling the <code>Device</code> by calling its methods.</li>
  <li><strong>AdvancedRemoteControl</strong>: Extends <code>RemoteControl</code>, adding a <code>mute</code> functionality, showcasing how high-level functionality can be added independently.</li>
  <li><strong>Client Code</strong>: Creates devices and remote controls, demonstrating that the remote can interact with any device through a consistent interface.</li>
</ol>

<p><strong>Bridge Pattern Example in Python: Shape and Color</strong></p>
<p>This example demonstrates the <strong>Bridge pattern</strong> applied to a hierarchy of shapes and colors. Using two separate hierarchies (Shape and Color), we can avoid creating redundant classes for each shape-color combination by composing shapes with colors independently.</p>

<img src="https://refactoring.guru/images/patterns/diagrams/bridge/problem-en-2x.png?id=c67b62720e0465821bbcb84debbbaab0">

<img src="https://refactoring.guru/images/patterns/diagrams/bridge/solution-en-2x.png?id=9439c9a85ac3db0399844b45fbbaecf6">
<p><strong>Step 1: Define the Color Hierarchy</strong></p>
<p>We’ll create a <code>Color</code> interface with subclasses <code>Red</code> and <code>Blue</code> to handle color-specific behavior.</p>

<p><strong>Step 2: Define the Shape Hierarchy</strong></p>
<p>The <code>Shape</code> hierarchy includes an abstract <code>Shape</code> class and concrete subclasses <code>Circle</code> and <code>Square</code>. The <code>Shape</code> class has a reference to a <code>Color</code> object, which acts as a bridge to the color implementation.</p>

<p><strong>Step 3: Combine Shape and Color</strong></p>
<p>Each <code>Shape</code> object can call the methods of its associated <code>Color</code> object to apply color-specific behavior.</p>

<p><strong>Python Implementation</strong></p>

```python
from abc import ABC, abstractmethod

# The Color interface (Implementer)
class Color(ABC):
    @abstractmethod
    def apply_color(self) -> str:
        pass

# Concrete Implementers
class Red(Color):
    def apply_color(self) -> str:
        return "Red"

class Blue(Color):
    def apply_color(self) -> str:
        return "Blue"

# The Shape abstract class (Abstraction)
class Shape(ABC):
    def __init__(self, color: Color):
        self.color = color
    
    @abstractmethod
    def draw(self) -> str:
        pass

# Concrete Shapes (Refined Abstraction)
class Circle(Shape):
    def draw(self) -> str:
        return f"Drawing a {self.color.apply_color()} Circle"

class Square(Shape):
    def draw(self) -> str:
        return f"Drawing a {self.color.apply_color()} Square"

# Client code
if __name__ == "__main__":
    red = Red()
    blue = Blue()

    red_circle = Circle(red)
    blue_circle = Circle(blue)
    red_square = Square(red)
    blue_square = Square(blue)

    print(red_circle.draw())   # Output: Drawing a Red Circle
    print(blue_circle.draw())   # Output: Drawing a Blue Circle
    print(red_square.draw())    # Output: Drawing a Red Square
    print(blue_square.draw())   # Output: Drawing a Blue Square
```

<p><strong>Explanation</strong></p>
<ol>
  <li><strong>Color Interface</strong>: <code>Color</code> is an abstract base class that defines the <code>apply_color</code> method, implemented by <code>Red</code> and <code>Blue</code>.</li>
  <li><strong>Shape Abstraction</strong>: <code>Shape</code> holds a reference to a <code>Color</code> object and has an abstract <code>draw</code> method, which is implemented by each shape (e.g., <code>Circle</code> and <code>Square</code>).</li>
  <li><strong>Concrete Shapes</strong>: <code>Circle</code> and <code>Square</code> classes use the <code>apply_color</code> method from their <code>Color</code> object to define the color of the shape when drawn.</li>
</ol>

<p><strong>Advantages of This Approach</strong></p>
<ul>
  <li><strong>Flexibility</strong>: New colors or shapes can be added independently. For example, adding a <code>Green</code> color won’t require creating new shape subclasses.</li>
  <li><strong>Reduced Complexity</strong>: The number of combinations is reduced since shapes and colors are handled independently, preventing an explosion of subclasses.</li>
</ul>


<p><strong>More Examples Using Python</strong></p>
<ul>
  <li><strong>Cross-Platform UI Rendering</strong>: An application interface that displays graphical elements on different platforms (Windows, Linux, macOS).</li>
  <li><strong>Media Players</strong>: A player interface that works with different types of media files (MP3, WAV, FLAC) with implementations for each file type.</li>
</ul>

<p>The Bridge Pattern helps maintain clear, modular code by separating high-level logic from detailed implementations, allowing each to be extended or modified independently without impacting the other.</p>


<br>
<br>

<h2>FlyWeight Design Pattern</h2>
<p><strong>Flyweight Design Pattern</strong></p>

<p>The Flyweight Pattern is a structural design pattern that minimizes memory usage by sharing as much data as possible with similar objects. This pattern is especially useful when an application has many objects that have common data or are very similar in their structure.</p>

<p><strong>1. What Is the Flyweight Pattern?</strong></p>

<p>In simpler terms, instead of creating multiple copies of the same object, we create a single shared object and reuse it wherever needed. It is like having a template that we reuse instead of creating a new template each time.</p>

<p><strong>2. Advantages for Developers</strong></p>

<ul>
    <li><strong>Reduced Memory Usage</strong>: Reuses objects instead of creating new ones, saving memory.</li>
    <li><strong>Improved Performance</strong>: Less memory usage leads to faster processing.</li>
    <li><strong>Simplified Object Creation</strong>: Allows handling a large number of small objects efficiently by using a centralized shared object.</li>
</ul>

<p><strong>3. When to Use the Flyweight Pattern</strong></p>

<ul>
    <li>When there are a large number of similar objects that can share data (e.g., multiple shapes in a graphic editor).</li>
    <li>When memory usage is a concern, and objects have some attributes that can be shared.</li>
    <li>When the cost of creating new objects is high, and object reuse can optimize performance.</li>
</ul>

<p><strong>4. Real-World Analogy</strong></p>

<p>Imagine a school where students wear uniforms. Instead of buying each student a unique uniform, the school issues a standard uniform that each student wears. Here, the uniform is shared among all students as a "template," while the students are like the objects that have unique characteristics (e.g., name, grade) but still share a common attribute (uniform).</p>

<p><strong>5. Real-Time Applications</strong></p>

<ul>
    <li><strong>Text Editors</strong>: Characters in a document can be represented by Flyweights, sharing common properties like font and color.</li>
    <li><strong>Graphics</strong>: Shapes in a graphics editor like lines, circles, or squares that have the same properties.</li>
    <li><strong>Games</strong>: In video games, objects like trees, stones, or houses are often rendered many times with the same appearance. Flyweight can share these similar objects.</li>
</ul>

<p><strong>6. Components Involved</strong></p>

<ol>
    <li><strong>Flyweight Interface</strong>: Declares methods that Flyweight classes should implement.</li>
    <li><strong>Concrete Flyweight</strong>: The class that implements the Flyweight interface and adds state if needed.</li>
    <li><strong>Flyweight Factory</strong>: Manages the Flyweight objects and ensures they’re shared and reused rather than creating new instances.</li>
    <li><strong>Client</strong>: Uses the Flyweight objects created by the Factory.</li>
</ol>

<p><strong>7. Steps to Implement the Flyweight Pattern</strong></p>

<ol>
    <li><strong>Identify Shared State</strong>: Separate common data (intrinsic state) from unique data (extrinsic state).</li>
    <li><strong>Create Flyweight Interface</strong>: Define operations required by Flyweight objects.</li>
    <li><strong>Implement Flyweight Class</strong>: Create a class that represents the shared data.</li>
    <li><strong>Flyweight Factory</strong>: Create a factory class that stores and reuses flyweight objects.</li>
    <li><strong>Use Flyweight in Client</strong>: When creating objects, request them from the factory instead of creating new ones.</li>
</ol>

<p><strong>8. Python Example</strong></p>

<p>Let’s build a Flyweight example in Python to represent circles in a graphics editor.</p>

<pre><code>
class Circle:
    def __init__(self, color):
        self.color = color  # Intrinsic state (shared)

    def draw(self, x, y, radius):
        print(f"Drawing Circle [Color: {self.color}, X: {x}, Y: {y}, Radius: {radius}]")

class CircleFactory:
    _circles = {}

    @staticmethod
    def get_circle(color):
        if color not in CircleFactory._circles:
            CircleFactory._circles[color] = Circle(color)
        return CircleFactory._circles[color]

# Client code to use Flyweight
def main():
    factory = CircleFactory()

    # Create circles with shared color
    red_circle = factory.get_circle("Red")
    red_circle.draw(10, 20, 5)

    red_circle2 = factory.get_circle("Red")
    red_circle2.draw(30, 40, 10)

    blue_circle = factory.get_circle("Blue")
    blue_circle.draw(15, 25, 8)

if __name__ == "__main__":
    main()
</code></pre>

<p><strong>Explanation</strong>:</p>

<ul>
    <li>The <strong>Circle</strong> class represents the Flyweight object with shared data (color).</li>
    <li><strong>CircleFactory</strong> is the Flyweight Factory that checks if a circle with the required color already exists; if not, it creates one and stores it.</li>
    <li><strong>Client Code</strong> uses the factory to get circles, minimizing the creation of new objects.</li>
</ul>

<p><strong>More Examples</strong></p>

<ul>
    <li><strong>Car Models in a Car Showroom</strong>: A Flyweight could represent cars with the same model and color. Only unique features (e.g., location, mileage) would differ.</li>
    <li><strong>Chess Board</strong>: For pieces like pawns or bishops, each type could be a flyweight and reused across the board.</li>
    <li><strong>Forest Simulation</strong>: Trees that share the same type and color could be Flyweights in a simulated forest.</li>
</ul>

<p>The Flyweight pattern helps avoid redundancy by sharing objects and improving efficiency in memory and processing.</p>

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
