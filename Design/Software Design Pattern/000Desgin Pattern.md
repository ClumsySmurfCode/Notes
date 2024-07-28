# Software design patterns

Software design patterns are typical solutions to common problems in software design. They represent best practices used by experienced object-oriented software developers. Design patterns can speed up the development process by providing tested, proven development paradigms.

### Categories of Design Patterns

1. **Creational Patterns**: Deal with object creation mechanisms, trying to create objects in a manner suitable to the situation. The basic form of object creation could result in design problems or added complexity to the design. Creational design patterns solve this problem by controlling this object creation.
    - **Singleton**: Ensures that a class has only one instance and provides a global point of access to it.
    - **Factory Method**: Defines an interface for creating an object, but lets subclasses alter the type of objects that will be created.
    - **Abstract Factory**: Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
    - **Builder**: Separates the construction of a complex object from its representation so that the same construction process can create different representations.
    - **Prototype**: Specifies the kinds of objects to create using a prototypical instance, and create new objects by copying this prototype.

2. **Structural Patterns**: Deal with object composition or structure. They help ensure that if one part of a system changes, the entire system doesn’t need to change.
    - **Adapter**: Allows incompatible interfaces to work together. It acts as a bridge between two incompatible interfaces.
    - **Bridge**: Separates an object’s interface from its implementation so the two can vary independently.
    - **Composite**: Composes objects into tree structures to represent part-whole hierarchies. Composite lets clients treat individual objects and compositions of objects uniformly.
    - **Decorator**: Attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality.
    - **Facade**: Provides a unified interface to a set of interfaces in a subsystem. Facade defines a higher-level interface that makes the subsystem easier to use.
    - **Flyweight**: Uses sharing to support large numbers of fine-grained objects efficiently.
    - **Proxy**: Provides a surrogate or placeholder for another object to control access to it.

3. **Behavioral Patterns**: Deal with communication between objects, what goes on between objects, and how they operate together.
    - **Chain of Responsibility**: Allows an object to pass the request along a chain of potential handlers until an object handles the request.
    - **Command**: Encapsulates a request as an object, thereby allowing for parameterization of clients with queues, requests, and operations.
    - **Interpreter**: Given a language, define a representation for its grammar along with an interpreter that uses the representation to interpret sentences in the language.
    - **Iterator**: Provides a way to access the elements of an aggregate object sequentially without exposing its underlying representation.
    - **Mediator**: Defines an object that encapsulates how a set of objects interact. Mediator promotes loose coupling by keeping objects from referring to each other explicitly.
    - **Memento**: Without violating encapsulation, captures and externalizes an object’s internal state so that the object can be restored to this state later.
    - **Observer**: Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
    - **State**: Allows an object to alter its behavior when its internal state changes. The object will appear to change its class.
    - **Strategy**: Defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it.
    - **Template Method**: Defines the skeleton of an algorithm in an operation, deferring some steps to subclasses. Template Method lets subclasses redefine certain steps of an algorithm without changing the algorithm’s structure.
    - **Visitor**: Represents an operation to be performed on the elements of an object structure. Visitor lets you define a new operation without changing the classes of the elements on which it operates.
```
Software Design Patterns
|
├── Creational Patterns
|   ├── Singleton
|   ├── Factory Method
|   ├── Abstract Factory
|   ├── Builder
|   └── Prototype
|
├── Structural Patterns
|   ├── Adapter
|   ├── Bridge
|   ├── Composite
|   ├── Decorator
|   ├── Facade
|   ├── Flyweight
|   └── Proxy
|
└── Behavioral Patterns
    ├── Chain of Responsibility
    ├── Command
    ├── Interpreter
    ├── Iterator
    ├── Mediator
    ├── Memento
    ├── Observer
    ├── State
    ├── Strategy
    ├── Template Method
    └── Visitor
```

### Example of a Design Pattern: Singleton Pattern

#### Intent
Ensure a class has only one instance and provide a global point of access to it.

#### Structure

```plaintext
+---------------------+
|     Singleton       |
+---------------------+
| - uniqueInstance    |<----------------+
| + getInstance()     |                 |
| + operation()       |                 |
+---------------------+                 |
     ^                                  |
     |                                  |
     +----------------------------------+
```

#### Implementation

```java
public class Singleton {
    // Create an instance of Singleton
    private static Singleton uniqueInstance;
    
    // Private constructor prevents instantiation from other classes
    private Singleton() {}

    // Get the unique instance of Singleton
    public static Singleton getInstance() {
        if (uniqueInstance == null) {
            uniqueInstance = new Singleton();
        }
        return uniqueInstance;
    }

    public void operation() {
        // Some operations
    }
}
```

### Usage

- **Singleton**: Logging, caching, thread pools, configuration settings.
- **Factory Method**: Creating instances of objects that are extended from a common base class.
- **Observer**: Event handling systems, such as GUI frameworks or messaging systems.

Design patterns provide solutions to common problems, which helps to standardize and simplify the development process. By understanding and utilizing these patterns, developers can create more robust, maintainable, and scalable software systems.
