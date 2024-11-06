<h1>UML (Unified Modeling Language)</h1>
<p><strong>UML (Unified Modeling Language)</strong> diagrams are visual tools used to show how different parts of a system work together. They help developers, designers, and stakeholders understand the structure, behavior, and interactions within a software project or system. Think of UML diagrams as blueprints for software; they simplify complex ideas, making it easier to plan, design, and communicate.</p>

<p>Here’s a breakdown of some common UML diagrams:</p>

<ul>
    <li><strong>Class Diagram</strong>
        <p><strong>What it does</strong>: Shows the structure of the system by displaying the classes (or types of objects) in it, along with their properties and methods (functions).</p>
        <p><strong>Example</strong>: Imagine a school software system with classes like <strong>Student</strong>, <strong>Teacher</strong>, and <strong>Course</strong>. Each class will have attributes (like <strong>name</strong> and <strong>age</strong> for Student) and methods (like <strong>enroll()</strong> for a Course).</p>
    </li>
    <li><strong>Use Case Diagram</strong>
        <p><strong>What it does</strong>: Shows who uses the system and what they can do with it.</p>
        <p><strong>Example</strong>: In an online shopping system, <strong>Customer</strong> can <strong>Browse Products</strong>, <strong>Add to Cart</strong>, and <strong>Checkout</strong>. Each of these actions is a "use case," showing what actions different users can perform.</p>
    </li>
    <li><strong>Sequence Diagram</strong>
        <p><strong>What it does</strong>: Shows the order of interactions between different parts of the system over time.</p>
        <p><strong>Example</strong>: In a login process, a sequence diagram could show the order of interactions: <strong>User</strong> enters login details → <strong>System</strong> checks details → <strong>User</strong> gets logged in.</p>
    </li>
    <li><strong>Activity Diagram</strong>
        <p><strong>What it does</strong>: Illustrates the flow of actions or steps in a process.</p>
        <p><strong>Example</strong>: In a cooking app, an activity diagram might show steps like <strong>Select Recipe</strong>, <strong>Gather Ingredients</strong>, <strong>Cook</strong>, and <strong>Serve</strong>.</p>
    </li>
    <li><strong>Component Diagram</strong>
        <p><strong>What it does</strong>: Breaks down the system into separate components and shows how they connect.</p>
        <p><strong>Example</strong>: For a website, components might include <strong>User Interface</strong>, <strong>Database</strong>, and <strong>Authentication Module</strong>, showing how they interact to provide functionality.</p>
    </li>
    <li><strong>State Diagram</strong>
        <p><strong>What it does</strong>: Shows the different states an object can be in and how it transitions between those states.</p>
        <p><strong>Example</strong>: In an online order system, an order might be in <strong>Created</strong>, <strong>Shipped</strong>, or <strong>Delivered</strong> states, with arrows showing how it moves from one state to another.</p>
    </li>
</ul>

<p><strong>Why UML Diagrams Are Useful</strong>:</p>

<ul>
    <li><strong>Clarity</strong>: Makes complex systems easier to understand.</li>
    <li><strong>Communication</strong>: Helps teams visualize the design and functionality.</li>
    <li><strong>Planning</strong>: Acts as a blueprint for building the actual system.</li>
</ul>

<p>In short, UML diagrams help visualize different parts of a system so everyone involved can understand and work together efficiently.</p>


<h2>Class Diagrams</h2>
<p>A Class Diagram is one of the main types of UML diagrams, used to show the structure of a system by modeling its classes, their attributes, operations (or methods), and the relationships between classes. Class diagrams provide a blueprint of how a system is organized and how its parts interact.</p>
<p>UML class diagram provides a static view of an object oriented system, showcasing its classes, attributes, methods, and the relationships among objects.</p>
<p><strong>Building Blocks of UML Class Diagrams</strong></p>
<h3>1.Class</h3>
<p>A class is a blueprint or template that defines the properties and behavior of an object.</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F494a65a0-c3aa-47fa-983e-1654b2b26d2f_1248x744.png">
<ul>
    <li><strong>Name (top compartment) : </strong>The unique identifier of the class (e.g., BankAccount)</li>
    <li><strong>Attributes (middle compartment) : The properties or data associated with the class (e.g., accountNumber, balance).</strong></li>
    <li><strong>Operations (bottom compartment): </strong>The actions or methods that can be performed by objects of the class (e.g., deposit(), updateBalance()).</li>
</ul>
<p><strong>Visibility Markers: </strong>Visibility markers indicate the accessibility of attributes and methods within a class.</p>
<ul>
    <li><strong>+ (Public): </strong>The attribute or method is accessible from any class.</li>
    <li><strong>- (Private):</strong>The attribute or method is only accessible within the same class.</li>
    <li><strong># (Protected):</strong>The attribute or method is accessible within the same class and its subclasses.</li>
    <li><strong>~ (Package):</strong>The attribute or method is accessible within the same package.</li>
</ul>
<h3>2.Attributes</h3>
<p>Attributes in a UML class diagram represent the properties or data fields of a class.</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F8ee29d85-a870-4ec1-92b8-9ecc245d425d_1248x520.png">
<p>Attributes are typically written in the format:</p>

```
visibility name: type [multiplicity] = defaultValue
```

<ul>
    <li><strong>Name:</strong>The name of the attribute.</li>
    <li><strong>Type:</strong>The data type of the attribute.</li>
    <li><strong>Multiplicity:</strong>Optional) Indicates how many instances of the type are allowed.</li>
    <li><strong>Default Value:</strong>he initial value of the attribute.</li>
</ul>

<h3>3.Methods</h3>
<p>Methods (or operations) in a UML class diagram represent the functions or behaviors that a class can perform.</p>
<p>Methods are typically written in the format:</p>

```
visibility name(parameterList): returnType
```

<ul>
    <li><strong>Name:</strong>The name of the method.</li>
    <li><strong>Parameter List:</strong>A comma-separated list of parameters, each specified as name: type.</li>
    <li><strong>Return Type:</strong>The data type returned by the method.</li>
</ul>

<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F75a17f88-fd67-45c3-940b-26418d5921ed_1474x520.png">

<h3>4.Interfaces</h3>
<p>An interface defines a contract for classes that implement it. It specifies a set of methods that the implementing classes must provide.</p>
<p>Interfaces are depicted as a class rectangle with the keyword «interface» above the interface name. Methods in interfaces are abstract by nature, so they are usually shown without any implementation details.</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff5a9233a-2083-4799-ba73-3fc57caeaead_834x448.png">

<h3>5.Abstract Class</h3>
<p>An abstract class is a class that cannot be instantiated (you can't create objects directly from it).</p>
<p>It serves as a blueprint for other classes (subclasses) that inherit from it.</p>
<p>An abstract class in UML is represented with the class name in italics and the keyword «abstract» above the class name. Abstract methods within the class are also typically shown in italics.</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fdeed8e70-5b57-446f-a53f-f474e86b5c98_932x528.png">

<h3>6.Enumeration</h3>
<p>An enumeration is a data type that defines a set of named values (e.g., colors, days of the week).</p>
<p>Enumerations, or enums, are represented with the keyword «enumeration» above the enumeration name. The values of the enumeration are listed within the class box.</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4e737467-b184-4e3b-b8dc-711ac7840b50_644x520.png">

<h3>7.Multiplicity</h3>
<p>Multiplicity specifies the number of instances of one class that can be related to a single instance of another class.</p>
<p>It is represented by a number or a range of numbers near the end of an association line.</p>
<ul>
    <li><strong>1</strong> Exctly Once</li>
    <li><strong>0..1</strong> Zero Or One</li>
    <li><strong>*</strong> Zero Or More</li>
    <li><strong>1..*</strong> One or More</li>
</ul>

<h3>Relationships in UML Class Diagrams</h3>
<p>There are six main types of relationships between classes: association, aggregation, composition, inheritance, implementation and dependency.</p>
<p>The arrows for the six relationships are as follows:</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0608aeaf-d32c-41e9-b7fa-6c105c27fab9_1032x648.png">

<h4>1.Association</h4>
<p>Association represents a "uses-a" relationship between two classes where one class uses or interacts with the other.</p>
<p><strong>Example : </strong>A Student class is associated with a Course class, as a student can enroll in multiple courses.</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F662eb8e0-7697-4a1c-8a2a-137e0d6879e9_1234x1380.png">

<h4>2. Aggregation</h4>
<p>Aggregation represents a "has-a" relationship where one class (the whole) contains another class (the part), but the contained class can exist independently.</p>
<p><strong>Example : </strong>A Car class has an Engine class but the Engine class can exist without the Car class.</p>
<img src="A Car class has an Engine class but the Engine class can exist without the Car class.">

<h4>3.Composition</h4>
<p>Composition represents a strong "has-a" relationship where the part cannot exist without the whole. If the whole is destroyed, the parts are also destroyed.</p>
<p><strong>Example : </strong> A House class is composed of Room class but the Room class can not exist without the House class.</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ffc9ef308-2a5e-4f8e-a61b-5835d6231b07_1552x376.png">

<h4>4.Inheritance</h4>
<p>Inheritance (or Generalization) represents an "is-a" relationship where one class (subclass) inherits the attributes and methods of another class (superclass).</p>
<p><strong>Example : </strong>A Dog class and a Cat class inherit from an Animal class, as both dogs and cats are animals.</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff92cd6a8-9454-4db5-8545-6b1f6c9ef1ff_1744x1186.png">

<h4>5.Realization (Implementation)</h4>
<p>Realization or implementation represents a relationship between a class and an interface, where the class implements the methods declared in the interface.</p>
<p><strong>Example: </strong>A Rectangle class and a Circle class implement the Shape interface, which declares a getArea() method.</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2b28dc2c-9bbe-4358-925e-5819bb81d722_1744x1234.png">

<h4>6.Dependency</h4>
<p>Dependency represents a "uses" relationship where a change in one class (the supplier) may affect the other class (the client).</p>
<p><strong>Example :</strong>A Customer class uses an Order class to place order.</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F1990f218-1fdd-45f5-8e23-62bf2dbcbb40_1956x456.png">

<h3>Combined Example</h3>
<p>Here's a comprehensive example that includes various types of relationships:</p>
<img src="https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F72d3654b-44b5-4708-a634-527534bd0937_3772x3040.png">
<p>The relationships between the classes are as follows:</p>
<ul>
    <li><strong>Inheritance: </strong>Dog and Cat inherit from Animal.</li>
    <li><strong>Realization/Implementation: </strong>Dog and Cat implement the Pet interface.</li>
    <li><strong>Aggregation: </strong>Person has an aggregation relationship with Pet, indicating that a person can have multiple pets.</li>
    <li><strong>Composition: </strong>Person has a composition relationship with Address, indicating that an address cannot exist without a person.</li>
    <li><strong>Association: </strong>Person has an association relationship with Phone, indicating that a person can have multiple phone numbers.</li>
    <li><strong>Dependency: </strong>Phone depends on the PhoneType enumeration for the phoneType attribute.</li>
</ul>

<p>Among the six types of relationships, the code structure of composition, aggregation, and association is the same, and it can be understood from the strength of the relationship. The order from strong to weak is: inheritance → implementation → composition → aggregation → association → dependency</p>


<h2>Use Case Diagram</h2>
<p>A Use Case Diagram in Unified Modeling Language (UML) is a visual representation that illustrates the interactions between users (actors) and a system. </p>
<p>It captures the functional requirements of a system, showing how different users engage with various use cases, or specific functionalities, within the system.</p>
<p>Use case diagrams provide a high-level overview of a system’s behavior, making them useful for stakeholders, developers, and analysts to understand how a system is intended to operate from the user’s perspective, and how different processes relate to one another. They are crucial for defining system scope and requirements.</p>
<p><strong>When to apply Use Case Diagram?</strong></p>
<ul>
    <li>When you need to gather and clarify user requirements, use case diagrams help visualize how different users interact with the system.</li>
    <li>If you’re working with diverse groups, including non-technical stakeholders, these diagrams provide a clear and simple way to convey system functionality.</li>
    <li>During the system design phase, use case diagrams help outline user interactions and plan features, ensuring that the design aligns with user needs.</li>
    <li>When defining what is included in the system versus what is external, use case diagrams help clarify these boundaries.</li>
</ul>
<h3>Use Case Diagram Notations</h3>
<p>UML notations provide a visual language that enables software developers, designers, and other stakeholders to communicate and document system designs, architectures, and behaviors in a consistent and understandable manner.</p>

<h4>1.Actors</h4>
<p>Actors are external entities that interact with the system. These can include users, other systems, or hardware devices. </p>
<p>In the context of a Use Case Diagram, actors initiate use cases and receive the outcomes. Proper identification and understanding of actors are crucial for accurately modeling system behavior.</p>
<p>Types: There are two types of actors:</p>
<ul>
    <li><strong>Primary Actor</strong>: The user who directly interacts with the system (e.g., a Customer using an e-commerce website).</li>
    <li><strong>Secondary Actor</strong>: A system or service that supports the primary actor's goals, typically indirectly (e.g., a Payment Processor in an online shopping system).</li>
</ul>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240129101834/Actor-(1).webp">

<h4>2.Use Cases</h4>
<p>Use cases are the actions or tasks that the system allows actors to perform.</p>
<p><strong>Examples: </strong>For a banking app, examples of use cases might include Check Balance, Transfer Funds, or Deposit Money.</p>
<p>In the online shopping system, examples of use cases could be “Place Order,” “Track Delivery,” or “Update Product Information”. Use cases are represented by ovals.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240129101909/Use-Case-.webp">

<h4>3.System Boundary</h4>
<p>The system boundary is a visual representation of the scope or limits of the system you are modeling. It defines what is inside the system and what is outside,showing what functions (use cases) the system supports.</p>
<p>The boundary helps to establish a clear distinction between the elements that are part of the system and those that are external to it.</p>
<p>The system boundary is typically represented by a rectangular box that surrounds all the use cases of the system.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240129101931/system.webp">

<h3>Relationships</h3>
<p>In a Use Case Diagram, relationships play a crucial role in depicting the interactions between actors and use cases.</p>
<h4>1.Association Relationship</h4>
<p>The Association Relationship represents a communication or interaction between an actor and a use case. It is depicted by a line connecting the actor to the use case. This relationship signifies that the actor is involved in the functionality described by the use case.</p>
<p><strong>Example: </strong>Online Banking System</p>
<ul>
    <li><strong>Actor</strong>Customer</li>
    <li><strong>Use Case</strong>Transfer Funds</li>
    <li><strong>Association</strong>A line connecting the “Customer” actor to the “Transfer Funds” use case, indicating the customer’s involvement in the funds transfer process.</li>
</ul>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240129101956/Association-(1).webp">

<h4>2.Includes</h4>
<p>The Include Relationship indicates that a use case includes the functionality of another use case.</p>
<p>It is denoted by a dashed arrow pointing from the including use case to the included use case. </p>
<p><strong>Example :</strong>Login might be an included use case in View Account Balance and Transfer Funds.</p>
<p><strong>Example :</strong>Social Media Platform</p>
<ul>
    <li><strong>Use Cases : </strong>Compose Post, Add Image</li>
    <li><strong>Include Relationship : </strong>The “Compose Post” use case includes the functionality of “Add Image.” Therefore, composing a post includes the action of adding an image.</li>
</ul>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240129102021/Include.webp">

<h4>3.Extends</h4>
<p></p>
<p>Shows optional functionality that extends the behavior of a use case. An extended use case is not always required but can add additional functionality.</p>
<p>The Extend Relationship illustrates that a use case can be extended by another use case under specific conditions.</p>
<p>It is represented by a dashed arrow with the keyword “extend.” This relationship is useful for handling optional or exceptional behavior.</p>
<p><strong>Example :</strong>An Order Food use case could have an Extend relationship to Apply Coupon, as applying a coupon is optional.</p>
<p><strong>Example :</strong>Flight Booking System</p>
<ul>
    <li><strong>Use Cases: </strong>Book Flight, Select Seat</li>
    <li><strong>Extend Relationship: </strong>The “Select Seat” use case may extend the “Book Flight” use case when the user wants to choose a specific seat, but it is an optional step.</li>
</ul>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240208135543/Extend.webp">

<h4>4.Generalization Relationship</h4>
<p>The Generalization Relationship establishes an “is-a” connection between two use cases, indicating that one use case is a specialized version of another. </p>
<p> It is represented by an arrow pointing from the specialized use case to the general use case.</p>
<p><strong>Example: </strong>Vehicle Rental System</p>
<ul>
    <li><strong>Use Cases: </strong>Rent Car, Rent Bike</li>
    <li><strong>Generalization Relationship: </strong>Both “Rent Car” and “Rent Bike” are specialized versions of the general use case “Rent Vehicle.”</li>
</ul>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240715131527/use_case_optimized_100.png">

<h3>Steps To Follow</h3>
<p><strong>To draw a Use Case Diagram in UML, follow these steps to effectively capture the system's functionality and interactions:</strong></p>

<ol>
    <li><strong>Identify Actors</strong>
        <ul>
            <li>Determine who interacts with the system. These can be:
                <ul>
                    <li><strong>Primary Actors:</strong> Users or systems that initiate actions within the system.</li>
                    <li><strong>Secondary Actors:</strong> External entities that support the primary actors.</li>
                </ul>
            </li>
            <li><strong>Example:</strong> For an online shopping system, actors might include <strong>Customer</strong>, <strong>Admin</strong>, and an external <strong>Payment Gateway</strong>.</li>
        </ul>
    </li>
    <li><strong>Identify Use Cases</strong>
        <ul>
            <li>Identify the main functionalities or actions the system needs to perform. These should represent specific tasks or goals.</li>
            <li><strong>Example:</strong> For an online shopping system, key use cases could include <strong>Browse Products</strong>, <strong>Add to Cart</strong>, <strong>Checkout</strong>, and <strong>Track Order</strong>.</li>
        </ul>
    </li>
    <li><strong>Connect Actors and Use Cases</strong>
        <ul>
            <li>Draw <strong>lines</strong> (called associations) between actors and the use cases they are involved in.</li>
            <li><strong>Example:</strong> Connect <strong>Customer</strong> to <strong>Browse Products</strong> and <strong>Checkout</strong>, indicating the <strong>Customer</strong> interacts with these functionalities.</li>
        </ul>
    </li>
    <li><strong>Add System Boundary</strong>
        <ul>
            <li>Draw a <strong>box</strong> around all use cases to define the scope of your system. This boundary clarifies what functionality is part of the system and what lies outside.</li>
            <li><strong>Label the box</strong> with the system name (e.g., "Online Shopping System") to identify it.</li>
        </ul>
    </li>
    <li><strong>Define Relationships</strong>
        <ul>
            <li>Use relationships to show connections between use cases:
                <ul>
                    <li><strong>Include:</strong> Indicates one use case is always required within another (e.g., <strong>Login</strong> might be included in <strong>Checkout</strong>).</li>
                    <li><strong>Extend:</strong> Shows optional functionality that extends the behavior of a use case (e.g., <strong>Apply Discount</strong> might extend <strong>Checkout</strong>).</li>
                </ul>
            </li>
            <li>Draw the relationships with appropriate notation:
                <ul>
                    <li>Dotted arrows labeled «include» or «extend» to indicate these special cases.</li>
                </ul>
            </li>
        </ul>
    </li>
    <li><strong>Review and Refine</strong>
        <ul>
            <li>Ensure that the diagram accurately reflects all interactions and relationships.</li>
            <li>Verify that each use case is necessary and all actor-use case connections make sense for the system requirements.</li>
        </ul>
    </li>
    <li><strong>Validate</strong>
        <ul>
            <li>Share the diagram with stakeholders for feedback. Ensure it aligns with their understanding and expectations.</li>
            <li>Make adjustments based on feedback to ensure clarity and completeness.</li>
        </ul>
    </li>
</ol>

<p><strong>Example Use Case Diagram for an Online Shopping System:</strong></p>
<ul>
    <li><strong>Actors:</strong>
        <ul>
            <li><strong>Customer:</strong> Main user of the system.</li>
            <li><strong>Admin:</strong> Manages products and sales.</li>
            <li><strong>Payment Gateway:</strong> Handles payment processing.</li>
        </ul>
    </li>
    <li><strong>Use Cases:</strong>
        <ul>
            <li><strong>Browse Products</strong>, <strong>Add to Cart</strong>, <strong>Checkout</strong>, <strong>Track Order</strong>, <strong>Manage Products</strong>, <strong>View Sales Report</strong>.</li>
        </ul>
    </li>
    <li><strong>Relationships:</strong>
        <ul>
            <li><strong>Include:</strong> <strong>Login</strong> is required for <strong>Checkout</strong> and <strong>Manage Products</strong>.</li>
            <li><strong>Extend:</strong> <strong>Apply Discount</strong> can optionally extend <strong>Checkout</strong>.</li>
        </ul>
    </li>
</ul>
<img src="https://images.wondershare.com/edrawmax/templates/use-case-diagram-for-online-shopping.png">

<h3>Common Mistakes</h3>

<p><strong>Avoiding common mistakes ensures the accuracy and effectiveness of the Use Case Diagram. Here are key points for each mistake:</strong></p>

<ul>
    <li><strong>Adding too much detail:</strong> Overloading the diagram with unnecessary information can confuse stakeholders and reduce clarity.</li>
    <li><strong>Unclear connections:</strong> Failing to clearly define associations between actors and use cases leads to misunderstandings about system interactions.</li>
    <li><strong>Inconsistent naming:</strong> Using different names for the same elements can create confusion and make the diagram harder to interpret.</li>
    <li><strong>Misusing generalization:</strong> Incorrectly applying generalization relationships can misrepresent how use cases and actors interact, distorting the diagram’s accuracy.</li>
    <li><strong>Undefined system boundaries:</strong> Not clearly defining the system boundary makes it hard to understand what functionality is inside or outside the system.</li>
    <li><strong>Treating the diagram as static:</strong> Failing to update the diagram as the system evolves can result in outdated and inaccurate representations.</li>
</ul>

<h3>Best Practices</h3>
<p><strong>Best Practices for Use Case Diagram</strong></p>

<p><strong>Crafting clear and effective Use Case Diagrams is essential for conveying system functionality and interactions. Here are some best practices to consider:</strong></p>

<ul>
    <li><strong>Focus on core functions:</strong> Capture the main functionalities without adding unnecessary details to keep the diagram clear and focused.</li>
    <li><strong>Consistent naming scheme:</strong> Use a uniform naming convention for actors and use cases throughout the diagram to avoid misunderstandings.</li>
    <li><strong>Standardized appearance:</strong> Ensure uniformity in the appearance of elements, such as ovals for use cases, stick figures for actors, and clear connecting lines, for a polished and professional presentation.</li>
    <li><strong>Organized use case groups:</strong> Group related use cases to represent distinct modules or subsystems within the larger system, aiding in readability and understanding.</li>
    <li><strong>Iterative updates:</strong> Regularly update the diagram as the system changes or new requirements emerge to keep it accurate and relevant.</li>
</ul>


<h2>Sequence Diagrams</h2>
<p>Sequence diagrams are a type of UML (Unified Modeling Language) diagram that visually represent the interactions between objects or components in a system over time.</p>
<p>They focus on the order and timing of messages or events exchanged between different system elements.</p>
<p>The diagram captures how objects communicate with each other through a series of messages, providing a clear view of the sequence of operations or processes.</p>
<p>Sequence diagrams are used because they offer a clear and detailed visualization of the interactions between objects or components in a system, focusing on the order and timing of these interactions.</p>

<h3>Sequence Diagram Notations</h3>
<h4>1.Actors</h4>
<p>Represent external entities interacting with the system, like users, devices, or other systems.</p>
<p>Displayed as stick figures on the left side of the diagram.</p>
<p>We use actors to depict various roles including human users and other external subjects.</p>
<p>We can have multiple actors in a sequence diagram.</p>
<p><strong>Example: </strong>Here the user in seat reservation system is shown as an actor where it exists outside the system and is not a part of the system. </p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240102164943/User-interacting-with-seat-reservation-system.jpg">

<h4>2.Lifelines</h4>
<p>A lifeline is a named element which depicts an individual participant in a sequence diagram. So basically each object in a sequence diagram is represented by a lifeline.</p>
<p>Lifeline elements are located at the top in a sequence diagram. The standard in UML for naming a lifeline follows the following format</p>

```
Instance Name : Class Name 
```

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228115925/Sequence-Diagrams.jpg">
<p>We display a lifeline in a rectangle called head with its name and type. The head is located on top of a vertical dashed line (referred to as the stem) as shown above.</p>
<p>If we want to model an unnamed instance, we follow the same pattern except now the portion of lifeline’s name is left blank.</p>
<p>Difference between a lifeline and an actor</p>
<ul>
    <li>A lifeline always portrays an object internal to the system whereas actors are used to depict objects external to the system.</li>
</ul>
<p>The following is an example of a sequence diagram:</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240102165110/Sequence-Diagram-223.jpg">

<h4>3.Messages</h4>
<p>Communication between objects is depicted using messages. The messages appear in a sequential order on the lifeline.</p>
<ul>
    <li>We represent messages using arrows.</li>
    <li>Lifelines and messages form the core of a sequence diagram.</li>
</ul>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240102165335/Different-Types-of-Messages.jpg">
<p>Messages can be broadly classified into the following categories:</p>
<ol>
    <li>Synchronous messages</li>
    <p>A synchronous message waits for a reply before the interaction can move forward. The sender waits until the receiver has completed the processing of the message. The caller continues only when it knows that the receiver has processed the previous message i.e. it receives a reply message.</p>
    <ul>
        <li>A large number of calls in object oriented programming are synchronous</li>
        <li>We use a solid arrow head to represent a synchronous message.</li>
    </ul>
    <img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228132950/Synchronus-Message-22.jpg">
    <li>Asynchronous Messages</li>
    <p>An asynchronous message does not wait for a reply from the receiver. The interaction moves forward irrespective of the receiver processing the previous message or not. We use a lined arrow head to represent an asynchronous message.</p>
    <img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228134039/Asynchronus-Message.jpg">
</ol>

<h4>4.Create message</h4>
<p>We use a Create message to instantiate a new object in the sequence diagram.</p>
<p>There are situations when a particular message call requires the creation of an object</p>
<p>It is represented with a dotted arrow and create word labelled on it to specify that it is the create Message symbol.</p>
<p><strong>Example :</strong>The creation of a new order on a e-commerce website would require a new object of Order class to be created. </p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240102165451/Create-Message.jpg">

<h4>5.Delete Message</h4>
<p>We use a Delete Message to delete an object.</p>
<p>When an object is deallocated memory or is destroyed within the system we use the Delete Message symbol.</p>
<p> It destroys the occurrence of the object in the system.It is represented by an arrow terminating with a x.</p>
<p><strong>Example: </strong>In the scenario below when the order is received by the user, the object of order class can be destroyed. </p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240102165540/Delete-Image.jpg">

<h4>6.Self Message</h4>
<p>Certain scenarios might arise where the object needs to send a message to itself. Such messages are called Self Messages and are represented with a U shaped arrow.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228134413/self-image-1.jpg">
<p><strong>Example: </strong>Consider a scenario where the device wants to access its webcam. Such a scenario is represented using a self message. </p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228134633/Self-Image-2.jpg">

<h4>7.Reply Message</h4>
<p>Reply messages are used to show the message being sent from the receiver to the sender. We represent a return/reply message using an open arrow head with a dotted line. The interaction moves forward only when a reply message is sent by the receiver.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228134838/Reply-Message.jpg">
<p><strong>Example: </strong>Consider the scenario where the device requests a photo from the user. Here the message which shows the photo being sent is a reply message. </p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228135137/Reply-Message-Example.jpg">

<h4>8.Found Message</h4>
<p>A Found message is used to represent a scenario where an unknown source sends the message. It is represented using an arrow directed towards a lifeline from an end point.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240102161203/found-message.jpg">
<p><strong>Example: </strong>Consider the scenario of a hardware failure. </p>
<p>It can be due to multiple reasons and we are not certain as to what caused the hardware failure.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228135840/found-message-example.jpg">

<h4>9.Lost Message</h4>
<p>A Lost message is used to represent a scenario where the recipient is not known to the system. It is represented using an arrow directed towards an end point from a lifeline.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228140024/lost-image.jpg">
<p>The warning might be generated for the user or other software/object that the lifeline is interacting with. Since the destination is not known before hand, we use the Lost Message symbol.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228140236/Lost-Image-Example.jpg">

<h4>10.Guards</h4>
<p>To model conditions we use guards in UML.</p>
<p>They are used when we need to restrict the flow of messages on the pretext of a condition being met. Guards play an important role in letting software developers know the constraints attached to a system or a particular process.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20231228140450/Guards.jpg">
<p>In order to be able to withdraw cash, having a balance greater than zero is a condition that must be met as shown below.</p>

<h3>Example</h3>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240103162001/Example-sequence-diagram-2.jpg">
<p><strong>The following sequence diagram depicts the process for an emotion-based music player:</strong></p>

<ol>
    <li><strong>Application is opened:</strong> The user opens the music player application.</li>
    <li><strong>Access to webcam:</strong> The device obtains permission to access the webcam.</li>
    <li><strong>Image capture:</strong> The webcam captures an image of the user.</li>
    <li><strong>Face detection and mood prediction:</strong> The device uses algorithms to detect the user's face and predict their mood based on the captured image.</li>
    <li><strong>Request for mood dictionary:</strong> The application sends a request to the database to retrieve a dictionary of possible moods.</li>
    <li><strong>Mood retrieval:</strong> The database returns the mood information to the application.</li>
    <li><strong>Display mood:</strong> The detected mood is displayed to the user on the application interface.</li>
    <li><strong>Music request:</strong> The application requests music related to the detected mood from the database.</li>
    <li><strong>Playlist generation:</strong> Based on the detected mood, a playlist is generated.</li>
    <li><strong>Playlist display:</strong> The generated playlist is shown to the user, ready to play.</li>
</ol>

<h3>Steps To Follow</h3>
<p><strong>Creating a Sequence Diagram</strong></p>
<p>Creating a sequence diagram involves several steps, and it’s typically done during the design phase of software development to illustrate how different components or objects interact over time. Here’s a step-by-step guide:</p>

<ol>
    <li><strong>Identify the Scenario:</strong> Understand the specific scenario or use case that you want to represent. This could be an interaction between objects or the flow of messages in a particular process.</li>
    <li><strong>List the Participants:</strong> Identify the participants (objects or actors) involved in the scenario. These can be users, systems, or external entities.</li>
    <li><strong>Define Lifelines:</strong> Draw a vertical dashed line for each participant to represent its existence over time. The lifeline shows the object’s presence during the interaction.</li>
    <li><strong>Arrange Lifelines:</strong> Position the lifelines horizontally in the sequence of their involvement, to visualize the flow of messages between participants.</li>
    <li><strong>Add Activation Bars:</strong> For each message, draw an activation bar on the sender’s lifeline to show the active time duration when the participant is processing the message.</li>
    <li><strong>Draw Messages:</strong> Use arrows between lifelines to represent messages. Messages can be synchronous (solid arrow), asynchronous (dashed arrow), or self-messages.</li>
    <li><strong>Include Return Messages:</strong> If a participant responds, draw a dashed arrow back to the original sender to represent the return message.</li>
    <li><strong>Indicate Timing and Order:</strong> Use numbers or sequence labels to show the order of messages. You can also use vertical dashed lines to indicate events or time progression.</li>
    <li><strong>Include Conditions and Loops:</strong> Use combined fragments for conditions (like if statements) and loops in the interaction, showing control flow complexity.</li>
    <li><strong>Consider Parallel Execution:</strong> If activities occur in parallel, draw parallel vertical dashed lines and place messages accordingly.</li>
    <li><strong>Review and Refine:</strong> Check the sequence diagram for clarity and accuracy. Refine as needed to ensure it represents the intended interaction.</li>
    <li><strong>Add Annotations and Comments:</strong> Include additional notes, annotations, or comments to clarify elements in the diagram.</li>
    <li><strong>Document Assumptions and Constraints:</strong> Note any assumptions or constraints related to the interaction alongside the diagram for future reference.</li>
    <li><strong>Tools:</strong> Use UML modeling tools or diagramming software to create a professional sequence diagram. These tools offer features for easy editing, collaboration, and documentation.</li>
</ol>


<h2>Activity Diagrams</h2>
<p>Activity diagram is essentially an advanced version of flow chart that modeling the flow from one activity to another activity.</p>
<p>Activity diagrams are an essential part of the Unified Modeling Language (UML) that help visualize workflows, processes, or activities within a system.</p>
<p>They depict how different actions are connected and how a system moves from one state to another.</p>
<p>By offering a clear picture of both simple and complex workflows, activity diagrams make it easier for developers and stakeholders to understand how various elements interact in a system.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240113165008/Unified-Modeling-Language-(UML)-Activity-Diagrams-(2).jpg">
<p>A basic activity diagram - flowchart like</p>
<img src="https://cdn-images.visual-paradigm.com/guide/uml/what-is-activity-diagram/02-basic-activity-diagram.png">

<h3>Activity Diagram Notations</h3>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112151723/Activity-Diagram-Notations.jpg">
<p><strong>1. Initial State</strong></p>
<p>The starting state before an activity takes place is depicted using the initial state.</p>
<p><strong>Symbol:</strong> A black filled circle.</p>
<p>This represents the entry point and the initial Activity State in a system.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112152513/initial-state.jpg">
<p><strong>Example:</strong> The initial state of the system before the application is opened.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112152912/Initial-State-symbol-being-used-(1).jpg">
<p><strong>2. Action or Activity State</strong></p>
<p>An activity represents execution of an action on objects or by objects. We represent an activity using a rectangle with rounded corners.</p>
<p><strong>Symbol:</strong> A rectangle with rounded corners.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112152950/activity-state.jpg">
<p><strong>Example:</strong> Opening an application is an activity state in the activity diagram.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112153109/Activity-State-symbol-being-used.jpg">

<p><strong>3. Action Flow or Control Flows</strong></p>
<p>Action flows or Control flows are used to show the transition from one activity state to another activity state.</p>
<p><strong>Symbol:</strong> A line with an arrowhead to depict a control flow.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112153109/Activity-State-symbol-being-used.jpg">
<p><strong>Example:</strong> Both states transit into one final state using action flow symbols (arrows).</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112153322/Using-Action-Flows-for-Transitions.jpg">

<p><strong>4. Decision Node and Branching</strong></p>
<p>When a decision is required before deciding the flow of control, a decision node is used. The outgoing arrows can be labelled with conditions or guard expressions.</p>
<p><strong>Symbol:</strong> A diamond shape.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112153442/decision-node.jpg">
<p><strong>Example:</strong> Applying conditions on the input number to display the result:</p>
<ul>
    <li>If the number is odd, display the number.</li>
    <li>If the number is even, display the error.</li>
</ul>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112153518/An-Activity-Diagram-using-Decision-Node.jpg">

<p><strong>5. Guard</strong></p>
<p>A Guard refers to a statement written next to a decision node on an arrow (sometimes within square brackets). The statement must be true for the control to shift along a particular direction.</p>
<p><strong>Symbol:</strong> A square bracket containing the guard expression.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112153635/guard.jpg">

<p><strong>6. Fork</strong></p>
<p>Fork nodes are used to support concurrent activities. The activities split into two parts and execute concurrently.</p>
<p><strong>Symbol:</strong> A rounded solid rectangular bar.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112153718/fork.jpg">
<p><strong>Example:</strong> In making coffee, the activity can be split into two concurrent activities.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112153750/A-Diagram-using-Fork-Notation.jpg">

<p><strong>7. Join</strong></p>
<p>Join nodes are used to support concurrent activities converging into one. It has two or more incoming edges and one outgoing edge.</p>
<p><strong>Symbol:</strong> A rounded solid rectangular bar with incoming edges and one outgoing edge.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112153918/join.jpg">
<p><strong>Example:</strong> When both activities, such as steaming the milk and adding coffee, are completed, they are converged into one final activity.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112154002/A-Diagram-using-Join-Notation.jpg">

<p><strong>8. Merge or Merge Event</strong></p>
<p>The merge notation is used when activities that are not executed concurrently need to be merged. Two or more activities merge into one.</p>
<p><strong>Symbol:</strong> A diamond shape.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112154002/A-Diagram-using-Join-Notation.jpg">
<p><strong>Example:</strong> A number can't be both odd and even at the same time, so two different paths merge into one.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112154111/An-Activity-Diagram-using-Merge-Notation-(1).jpg">

<p><strong>9. Swimlanes</strong></p>
<p>Swimlanes group related activities into one column or row, often used to add modularity to the diagram.</p>
<p><strong>Symbol:</strong> A rectangular column or row.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112154155/swimlane.jpg">
<p><strong>Example:</strong> Different activities based on whether the number is odd or even are grouped into separate swimlanes.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112154228/An-Activity-Diagram-making-use-of-Swimlanes.jpg">

<p><strong>10. Time Event</strong></p>
<p>A time event refers to an event that stops the flow for a period. An hourglass symbol depicts it.</p>
<p><strong>Symbol:</strong> An hourglass symbol.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112154305/time-event.jpg">
<p><strong>Example:</strong> Processing an image takes time, and it is represented using the time event notation.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112154337/An-Activity-Diagram-using-Time-Event-Notation.jpg">

<p><strong>11. Final State or End State</strong></p>
<p>The final state represents the end of the process or activity. It is depicted using a filled circle within a circle.</p>
<p><strong>Symbol:</strong> A filled circle within a circle.</p>
<p><strong>Example:</strong> The system reaches the final state after completing a process or activity.</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240112154422/final-state.jpg">

<h3>Example-1</h3>
<p><strong>The following activity diagram example describes the workflow for a word processor to create a document through the following steps:</strong></p>

<ol>
    <li><strong>Open the word processing package:</strong> The user opens the word processing software.</li>
    <li><strong>Create a file:</strong> A new file is created within the word processor.</li>
    <li><strong>Save the file under a unique name:</strong> The user saves the file under a unique name in the directory.</li>
    <li><strong>Type the document:</strong> The user types the content of the document.</li>
    <li><strong>If graphics are necessary:</strong> 
        <ul>
            <li><strong>Open the graphics package:</strong> The user opens the graphics software.</li>
            <li><strong>Create the graphics:</strong> The user creates the necessary graphics.</li>
            <li><strong>Paste the graphics into the document:</strong> The created graphics are pasted into the word processing document.</li>
        </ul>
    </li>
    <li><strong>If a spreadsheet is necessary:</strong> 
        <ul>
            <li><strong>Open the spreadsheet package:</strong> The user opens the spreadsheet software.</li>
            <li><strong>Create the spreadsheet:</strong> The user creates the necessary spreadsheet.</li>
            <li><strong>Paste the spreadsheet into the document:</strong> The created spreadsheet is pasted into the word processing document.</li>
        </ul>
    </li>
    <li><strong>Save the file:</strong> The user saves the document after including graphics or spreadsheet if necessary.</li>
    <li><strong>Print a hard copy of the document:</strong> The user prints a physical copy of the document.</li>
    <li><strong>Exit the word processing package:</strong> The user exits the word processing software after completing the tasks.</li>
</ol>

<img src="https://cdn-images.visual-paradigm.com/guide/uml/what-is-activity-diagram/03-activity-diagram-word-processor-example.png">

<h3>Example-2</h3>
<p><strong>Activity Diagram: Process Order</strong></p>

<p><strong>Problem Description:</strong> Once the order is received, the activities split into two parallel sets of activities. One side fills and sends the order, while the other handles the billing. On the "Fill Order" side, the method of delivery is decided conditionally. Depending on the condition, either the "Overnight Delivery" activity or the "Regular Delivery" activity is performed. Finally, the parallel activities combine to close the order.</p>

<ol>
    <li><strong>Receive the Order:</strong> The order is received from the customer.</li>
    <li><strong>Split into Parallel Activities:</strong>
        <ul>
            <li><strong>Fill and Send Order:</strong> The first parallel activity that involves filling and shipping the order.</li>
            <li><strong>Handle Billing:</strong> The second parallel activity that processes the billing for the order.</li>
        </ul>
    </li>
    <li><strong>Decide Delivery Method (Conditional):</strong>
        <ul>
            <li><strong>Overnight Delivery:</strong> If the condition is met (e.g., expedited shipping), the overnight delivery activity is performed.</li>
            <li><strong>Regular Delivery:</strong> If the condition is not met, regular delivery is performed instead.</li>
        </ul>
    </li>
    <li><strong>Complete the Order:</strong> Both the "Fill and Send Order" and "Handle Billing" parallel activities are completed and combined.</li>
    <li><strong>Close the Order:</strong> The order is finalized, and the process ends.</li>
</ol>

<img src="https://cdn-images.visual-paradigm.com/guide/uml/what-is-activity-diagram/04-activity-diagram-example-process-order.png">

<h3>Example-3</h3>
<p><strong>Activity Diagram: Student Enrollment in University</strong></p>

<p><strong>Problem Description:</strong> This UML activity diagram describes the process for student enrollment in a university.</p>

<ol>
    <li><strong>Applicant Wants to Enroll:</strong> The applicant expresses their intent to enroll in the university.</li>
    <li><strong>Hand in Filled Enrollment Form:</strong> The applicant submits a filled-out copy of the enrollment form to the registrar.</li>
    <li><strong>Registrar Inspects the Forms:</strong> The registrar checks the enrollment form to ensure it is completed correctly.</li>
    <li><strong>Registrar Determines Proper Form Completion:</strong> The registrar determines whether the form has been filled out properly.</li>
    <li><strong>Inform the Student About University Overview:</strong> If the form is complete, the registrar informs the student to attend the university overview presentation.</li>
    <li><strong>Help Student Enroll in Seminars:</strong> The registrar assists the student in selecting and enrolling in seminars.</li>
    <li><strong>Ask Student to Pay Initial Tuition:</strong> The registrar requests the student to pay for the initial tuition to complete the enrollment process.</li>
</ol>
<img src="https://cdn-images.visual-paradigm.com/guide/uml/what-is-activity-diagram/05-activity-diagram-example-student-enrollment.png">


<h3>Steps To Follow</h3>
<p><strong>Step 1: Identify the Initial State and Final States</strong></p>
<p>This is like setting the starting point and ending point of a journey. Identify where your process begins (initial state) and where it concludes (final states).</p>
<p><strong>Example:</strong> If you are modeling a process for making a cup of tea, the initial state could be "No tea prepared," and the final state could be "Tea ready."</p>

<p><strong>Step 2: Identify the Intermediate Activities Needed</strong></p>
<p>Think of the steps or actions required to go from the starting point to the ending point. These are the activities or tasks that need to be performed.</p>
<p><strong>Example:</strong> Continuing with the tea-making, intermediate activities could include "Boil water," "Pour tea into a cup."</p>

<p><strong>Step 3: Identify the Conditions or Constraints</strong></p>
<p>Consider the conditions or circumstances that might influence the flow of your process. These are the factors that determine when you move from one activity to another.</p>
<p><strong>Example:</strong> Using the tea-making scenario, a condition could be "Water is boiled," which triggers the transition to the next activity.</p>

<p><strong>Step 4: Draw the Diagram with Appropriate Notations</strong></p>
<p>Now, represent the identified states, activities, and conditions visually using the appropriate symbols and notations in an activity diagram. This diagram serves as a visual map of your process, showing the flow from one state to another.</p>
