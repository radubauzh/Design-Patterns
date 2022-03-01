## Overview

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

## Singleton
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

## Singleton

**Advantages**


**Disadvantages**
