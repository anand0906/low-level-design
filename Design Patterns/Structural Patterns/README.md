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
class MediaPlayer:
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
class MediaPlayer:
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
class VideoPlayer:
    def play(self, video_id):
        pass
    
    def pause(self):
        pass
    
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


