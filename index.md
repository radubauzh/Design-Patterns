# Overview

### Design Patterns which I cover on this page
1. Inheritance
2. Singleton Design Pattern
3. Adapter Design Pattern
4. Composite Design Pattern
5. Observer Design Pattern
6. Command Design Pattern
7. State Design Pattern
8. Decorator Design Pattern
9. Strategy Design Pattern
10. Iterator Design Pattern
11. MVC Design Pattern

### What is a Design Pattern?

A Design Pattern is a pattern that captures a solution to a recurring design problem
- It is not a pattern for implementation problems
- It is not a ready-made solution that has to be applied
A design pattern is a description of communicating objects and classes that are customized to solve a general design problem in a particular context.
A design pattern is a kind of blueprint
A design pattern Consists of different parts
- All of these parts make up the pattern!
- When we talk about the pattern we therefore mean all of these parts together (not only the class diagram..)

### Why design patterns?
**Smart**
- Elegant solutions that a novice would not think of 
**Generic**
- Independent on specific system type, language
- Although slightly biased towards C++ Well-proven
- Successfully tested in several systems 
**Simple**
- Combine them for more complex solutions 
**Well-known**
- Can be used to communicate complex ideas more easily

## Inheritance

**Advantages**
Minimize the amount of duplicate code in an application by sharing common code amongst several subclasses
Where equivalent code exists in two related classes, the hierarchy can usually be refactored to move the common code up to a mutual superclass. This also tends to result in a better organization of code and smaller, simpler compilation units.
- **Reusability:** facility to use public methods of superclass without rewriting the same in subclasses
- **Extensibility:** extending and deriving of new classes from existing classes
- **Data hiding:** superclass can decide to keep some data private so that it cannot be altered by the subclasses
**Overriding:** superclass functions can be overwritten in subclasses, so that meaningful implementation of the superclass method can be designed in the subclass Java **fields** are initialized from the declaration of the most general super-class down to the most specific class.


**Disadvantages**
- Dependency: two classes (super and sub) get tightly coupled. This means if we change code in super class it will get affects to all sub classes which are inheriting the super class code.
- Maintenance: Every time you create a new sub class, you have to look at and possibly overwrite every method defined in the super class.
- Problems when new sub class does not have behaviour of super class. E.g. RubberDuck can not fly() -> you need to overwrite the method in the sub class to do nothing -> not a good solution -> better: use interface Flyable (Problem with interface: completely destroys the reuse for those behaviours, so it just creates a different maintenance nightmare. E.g. imagine you want to make a little change to the flying behaviour.. in all 48 of the flying Duck subclasses. )

## Singleton Design Pattern
The Singleton Pattern ensures a class has only one instance and provides a global point of access to it.

**Advantages**
- Singleton instance fields don’t take up space in the global namespace
- Singletons may be lazily initialized (to be discussed further)

**Disadvantages**
- Singleton causes code to be tightly coupled. The singleton object is exposed globally and is available to a whole application. Thus, classes using this object become tightly coupled; any change in the global object will impact all other classes using it.
- They hide dependencies instead of exposing them.
- Singleton Pattern does not support inheritance
- Singleton principle can be violated by techniques such as cloning. If an application is running on multiple JVM’s, then, in this case, Singleton might be broken.

**Singleton vs. static method**
- Static classes don’t promote inheritance.
- You cannot specify any creation logic with static methods

```markdown
public static Singleton getInstance() {
  if (uniqueInstance == null) {
    synchronized (Singleton.class) {
      if (uniqueInstance == null) {
        uniqueInstance = new Singleton();
```


## Adapter Design Pattern
Adapter lets classes work together that couldn’t otherwise because of incompatible interfaces.
The Adapter Pattern **converts the interface of a class into another interface** the client expect.
**Advantages**
- Single Responsibility Principle. You can separate the interface or data conversion code from the primary business logic of the program.
- Open/Closed Principle. You can introduce new types of adapters into the program without breaking the existing client code, as long as they work with the adapters through the client interface.

**Disadvantages**
- The overall complexity of the code increases because you need to introduce a set of new interfaces and classes. Sometimes it’s simpler just to change the service class so that it matches the rest of your code.

## Observer Design Pattern
The Observer Pattern defines a one-to-many dependency between objects to that when one object changes state, all of its dependents are notified and updates automatically.

The observer pattern provides an object design where subjects and observers are loosely coupled. Why?
- The only thing the subject knows about an observer is that is implements a certain interface.
- We can add/remove observers at any time (also in runtime)
- We never need to modify the subjects to add new types of observers
- We can reuse subjects or observers independently of each other
- Changes to either the subject or an observer will not affect the other
- Loosely coupled designs allow us to build flexible OO systems that can handle change because they minimize the interdependency between objects.

**Advantages**
- Open/Closed Principle. You can introduce new subscriber classes without having to change the publisher’s code (and vice versa if there’s a publisher interface).
- You can establish relations between objects at runtime.

**Disadvantages**
- Subscribers are notified in random order

**Examples**
Newspapers, Digital Clock, MVC Pattern, Datatable

## Command Design Pattern
The Command Pattern encapsulates a request as an object, thereby letting you parameterize other objects with different requests, queue or log requests, and support undoable operations.

**Advantages**
- Single Responsibility Principle. You can decouple classes that invoke operations from classes that perform these operations.
- Open/Closed Principle. You can introduce new commands into the app without breaking existing client code.
- You can implement undo/redo.
- You can implement deferred execution of operations.
- You can assemble a set of simple commands into a complex one.

**Disadvantages**
- The code may become more complicated since you’re introducing a whole new layer between
 
 
 ## Iterator Design Pattern
The Iterator Pattern provides a way to access the internal objects of an aggregate object sequentially without exposing anything about the internal structure of the encapsulation object. It provides access to a collection of objects encapsulated within another object without violating it’s encapsulation property
**Advantages**
- Single Responsibility Principle. You can clean up the client code and the collections by extracting bulky traversal algorithms into separate classes.
- Open/Closed Principle. You can implement new types of collections and iterators and pass them to existing code without breaking anything.
- You can iterate over the same collection in parallel because each iterator object contains its own iteration state.
- For the same reason, you can delay an iteration and continue it when needed.


**Disadvantages**
- Applying the pattern can be an overkill if your app only works with simple collections.
- Using an iterator may be less efficient than going through elements of some specialized collections directly.

 ## State Design Pattern
The State Pattern allows an object to alter its behavior when its internal state changes. The object will appear to change its class.
**Advantages**
- Flexible
- Single Responsibility Principle. Organize the code related to particular states into separate classes.
- Open/Closed Principle. Introduce new states without changing existing state classes or the context.
- Simplify the code of the context by eliminating bulky state machine conditionals.
**Disadvantages**
- Applying the pattern can be overkill if a state machine has only a few states or rarely changes.

## Composite Design Pattern
The Composite Pattern allows you to compose objects into tree structures to represent part-whole hierarchies. Composite lets clients treat individual objects and compositions of objects uniformly. (leaves)
**Advantages**
- You can work with complex tree structures more conveniently: use polymorphism and recursion to your advantage.
- Open/Closed Principle. You can introduce new element types into the app without breaking the existing code, which now works with the object tree.

**Disadvantages**
- It might be difficult to provide a common interface for classes whose functionality differs too much. In certain scenarios, you’d need to overgeneralize the component interface, making it harder to comprehend.
- The Composite Pattern allows us to build structures of objects in the form of trees that contain both compositions of objects and individual objects as nodes.
- Using a composite structure, we can apply the same operations over both composites and individual objects.
- In other words, in most cases we can ignore the differences between compositions of objects and individual objects


## Strategy Design Pattern
The Strategy Pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it.

**Advantages**
- You can swap algorithms used inside an object at runtime.
- You can isolate the implementation details of an algorithm from the code that uses it.
- You can replace inheritance with composition.
- Open/Closed Principle. You can introduce new strategies without having to change the context.

**Disadvantages**
- If you only have a couple of algorithms and they rarely change, there’s no real reason to overcomplicate the program with new classes and interfaces that come along with the pattern.
- Clients must be aware of the differences between strategies to be able to select a proper one.
- A lot of modern programming languages have functional type support that lets you implement different versions of an algorithm inside a set of anonymous functions. Then you could use these functions exactly as you’d have used the strategy objects, but without bloating your code with extra classes and interfaces.

## Decorator Design Pattern
The Decorator Pattern attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality.
**Advantages**
- You can extend an object’s behavior without making a new subclass.
- You can add or remove responsibilities from an object at runtime.
- You can combine several behaviors by wrapping an object into multiple decorators. 
- Single Responsibility Principle. You can divide a monolithic class that implements many possible variants of behavior into several smaller classes.


**Disadvantages**
- It’s hard to remove a specific wrapper from the wrappers stack.
- It’s hard to implement a decorator in such a way that its behavior doesn’t depend on the order in the decorators stack.
- The initial configuration code of layers might look pretty ugly.



## Compound Pattern - MVC
It is a common architectural pattern which is used to design and create interfaces and the structure of an application. This pattern divides the application into three parts that are dependent and connected to each other. These designs are used to distinguish the presentation of data from the way the data is accepted from the user to the data that is being shown.

**Advantages**
- Multiple views can be made to models
- The partition of duties helps the developer in future developments and upgradations.
- The MVC theory works have low coupling behavior among the models, views, and controllers.
- Multiple developers can work on models, views, and controllers at the same time
- The views for a required model are grouped together.



```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

## Design Pattern

**Advantages**


**Disadvantages**
