# SOLID 
SOLID is a collection of important programming practices that were developed by Robert C. Martin. One of the most popular sets of design principles in object-oriented software development. It’s a mnemonic acronym for the following five design principles:
S: Single Responsibility Principle
O: Open/Closed Principle
L: Liskov Substitution Principle
I: Interface Segregation Principle
D: Dependency Inversion

SOLID consists of below coding practices:
SRP - Single responsibility principle
OCP - Open/close principle
LSP - Liskov substitution principle
ISP - Interface segregation principle
DIP - Dependency inversion principle

# SRP - Single responsibility principle
The project demonstrates the popular software design principle i.e. Single Responsibility Principle. The SRP principle is a part of S.O.L.I.D. principles which represents first letter S.  SRP - says that each method / class should be responsible for one specific activity. Inserting everything into one method does not meet the basic assumptions of objectivity, but also makes it difficult to read, repair or expand programs. The principle states, A class should have only one reason to change. OR A class should have only one responsibility. So, a class should perform only one task, which makes it easier to read, maintain, test, debug and many more benefits.

This principle is very noticeable when we write an application that begins to grow with time. It is enriched with new functionalities. Then we want to use already existing classes and their capabilities. However, it turns out, that the class that A should do is also do B, C and D, which is not desired by the currently created implementation. Then the problem arises because we can no longer use the given class. In this situation, you can avoid sticking to the SRP.

I have implemented a simple e-commerce application. This project is not about how an e-commerce web-site works, it just explains the idea behind Single Responsibility Principle. The application performs only two tasks:

Place an order.
Calculate bill for the placed order.
As you can see I have implemented both the services in separate classes i.e. PlaceOrderService and CalculateBillService. PlaceOrderService receives purchased items list as an input and places the order. So the class performs only one task. In other words, it has only one responsibility, just to place the order. Only one responsibility doesn't mean you should have only one method in a single class. If multiple methods are implemented to define a single functionality, such as "Placing the Order". Then the class design does not violate the rules of SRP.

If we talk about beans I have used. they also define only one task i.e. they define their properties and their behavior. There is no other business logic inside them.

Same thing we can say about the controller classes.

# OCP - Open/close principle
The OCP principle is a part of S.O.L.I.D. principles which represents second letter O.  The OCP principle says that the classes that we create are open to extensions and closed to modifications. The principle states, Software entities like modules, classes, functions should be Open For Extension but Closed for Modification. Which means a software entities should be designed in such a way, so the existing code should not be modified rather it can be scaled. That means we must provide abstract implementation rather than concrete such as make use of interfaces.

The application that we create must be ready for extensions, because the systems are changing very quickly these days. Thanks to the OCP principle, we are able to repeatedly use our classes for various tasks, which promotes reusability of the code, but also makes it easy to understand.

Before explaining the project, let's take an example

The project demonstrates the principle using an example of shapes. There is an interface ShapeArea which have a method named calculateArea(). The job of this method is to calculate the area, no matter what kind of shape it is.

In this project, the method calculateArea() can be used to calculate area of any shape. A class just need to provide the definition of calculateArea() according to the shape. So, the interface ShapeArea is open for extension but closed for modification.

# LSP - Liskov substitution principle
The project demonstrates the popular software design principle i.e. Liskov Substitution Principle. The LSP principle is a part of S.O.L.I.D. principles which represents third letter L. The principle states, In a computer program, if S is a subtype of T, then objects of type T may be replaced with objects of type S (i.e., objects of type S may substitute objects of type T) without altering any of the desirable properties of that program (correctness, task performed, etc.)

LSP also can be described as, Methods that use references to the base classes must be able to use the objects of the derived classes without knowing it. In simple words, derived classes must be substitutable for the base class.

The project demonstrates the principle using an example of dancers and non dancers where there super class is people. If we define the dance() method in People class then the class will break when Non Dancers instantiate it. So, the solution is to separate the properties and create a hierarchy in such way so that Super Class shouldn't be modified later. Violation of LSP is also violation of Open closed Principle. Functions that use pointers or references to base classes must also be able to use class objects that inherit from the base classes without having a thorough knowledge of these objects.

# ISP - Interface segregation principle
The ISP principle is a part of S.O.L.I.D. principles which represents fourth letter I. ISP says: "Many dedicated interfaces are better than one overall". 

When we design an application we should take care how we are going to make abstract module which contains several submodules. Considering module implemented by a class, we can have an abstraction of system done in an interface. But if we want to extend our application adding another module that contains only some of the submodules of original system, we are forced to implement the full interface and to write some dummy methods. Such an interface is named fat interface or polluted interface. Having an interface pollution is not a good solution and might induce inappropriate behavior in the system.

The principle states, Clients should not be forced to implement interfaces they don't use. Instead of one fat interface many small interfaces are preferred based on groups of methods, each one serving one submodule.

Problem :
In this project, if all three interfaces i.e. Jumpers, Racers and Swimmers were in a single interface. Then the Classes which are implmenting this single interface would have to implement the methods they don't require. For example, Racers class had to implement methods like jump() and swim() which is not needed.

Solution :
So, in this project, the single interface is separated into 3 more interfaces i.e. Jumpers, Swimmers and Racers.

The interface should give a specific shape to the class, and the methods that must be implemented within the class should be common to all implementation classes.

# DIP - Dependency inversion principle
The DIP principle is a part of S.O.L.I.D. principles which represents fifth letter D.

As a Java programmer, you’ve likely heard about code coupling and have been told to avoid tightly coupled code. Ignorance of writing “good code” is the main reason of tightly coupled code existing in applications. As an example, creating an object of a class using the new operator results in a class being tightly coupled to another class. Such coupling appears harmless and does not disrupt small programs. But, as you move into enterprise application development, tightly coupled code can lead to serious adverse consequences.

Usually abstraction means an abstract class or interface. Essentially, introducing a certain abstraction allows us to exchange individual elements of program with other ones more suitable for a specific task. We try not to enter into classes depending on its smaller parts. When one class knows explicitly about the design and implementation of another class, changes to one class raise the risk of breaking the other class. Such changes can have rippling effects across the application making the application fragile. To avoid such problems, you should write “good code” that is loosely coupled, and to support this you can turn to the Dependency Inversion Principle.

The principle states,
A. High-level modules should not depend on low-level modules. Both should depend on abstractions.
B. Abstractions should not depend on details. Details should depend on abstractions.

Conventional application architecture follows a top-down design approach where a high-level problem is broken into smaller parts. In other words, the high-level design is described in terms of these smaller parts. As a result, high-level modules that gets written directly depends on the smaller (low-level) modules.

What Dependency Inversion Principle says is that instead of a high-level module depending on a low-level module, both should depend on an abstraction. Let us look at it in the context of Java through this figure.

Problem :
In this project, if we hardcode JavaEditor class into IDE class. Then the IDE is bound to only edit Java specific code. We don't want that. The IDE must be able to edit any language code.

Solution :
So, the solution is to make an abstraction of Editor as an interface and both IDE and JavaEditor or CppEditor depends on Editor interface. Now IDE is able to edit any code.

# YAGNI - You ain’t gonna need it
The principle says not to create functionality until it is actually needed. This is a good practice because we do not create redundancy in the application and we do not leave code that is not used in any way.

YAGNI on Wiki: https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it

# DRY - Don’t repeat yourself
Analysis of the written code and the desire to improve it are always key in software writing.

When writing several classes with similar properties, we may encounter similar problems. This is a sign that the code inside these classes is common and it may indicate that it should be separated into another class that will deal with repetitive tasks in one place. Thanks to this operation, both classes will use the same code, and thus, the probability of error will drop.

DRY on Wiki: https://en.wikipedia.org/wiki/Don%27t_repeat_yourself

# KISS - Keep It Simple, Stupid!
This rule is often mentioned when discussing architecture or details of building projects. Its essence is striving to maintain an elegant and transparent structure, without adding unnecessary elements.

KISS on Wiki: https://en.wikipedia.org/wiki/KISS_principle

# SOC - Separation of Concern
The separation of issues consists in the division of the program into separate modules that overlap with as little functionality as possible. We call this kind of program modular. Each element of the system should have its separate and singular application. The purpose of SoC (Separation of Concern) is to create a system in which each part plays a significant role while maintaining the possibility of maximum adaptation to changes. SoC does not refer only to the system architecture, but to various issues, eg to divide the application into layers (presentation, business logic, access to data, database).

SOC on Wiki: https://en.wikipedia.org/wiki/Separation_of_concerns

# CQS - Command Query Separation
It is a rule that says that every method in the system should be classified into one of two groups:

Command - these are methods that change the state of the application and do not return anything.
Query - these are methods that return something, but do not change the state of the application.

CQS on Wiki: https://en.wikipedia.org/wiki/Command%E2%80%93query_separation

# More:
https://howtodoinjava.com/best-practices/5-class-design-principles-solid-in-java/ <br/>
https://www.freecodecamp.org/news/kriptofolio-app-series-part-1/ <br/>
https://itnext.io/solid-principles-explanation-and-examples-715b975dcad4 <br/>
https://roadmap.sh/guides/design-patterns-for-humans <br/>
