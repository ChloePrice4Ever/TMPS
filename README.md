# TMPS_lab_1 - Calculator app in C#
By Ciumac Nichita

Task : Build an app that will follow SOLID Principles using an OOP programing language
General Theory :

S - Single Responsibility Principle: a class should have only one reason to change.

O - Open/Closed Principle: entities should be open for extension but closed for modification.

L - Liskov Substitution Principle: subtypes must be substitutable for their base types.

I - Interface Segregation Principle: clients should not be forced to depend on interfaces they do not use.

D - Dependency Inversion Principle: high-level modules should not depend on low-level modules. Both should depend on abstractions.

For this task I decided to create a simple calculator application that will follow all these principles and be easy to implement using c# language.

This code is a simple implementation of a calculator that takes two numbers and an operation, and returns the result of applying that operation to the two numbers.

The IOperation interface defines a single Calculate method that accepts two double parameters and returns a double result. This interface is implemented by four different classes - Addition, Subtraction, Multiplication, and Division, each of which provides an implementation of the Calculate method corresponding to the corresponding mathematical operation.

The Calculator class has a single constructor that receives an object that implements the IOperation interface and stores it in a private field. The class also has a Calculate method that calls the IOperation object's Calculate method to perform the appropriate operation and returns the result.

In the Main method, the user is first prompted to enter the two numbers and the desired operation. Based on the value entered for the operation, an instance of one of the four operation classes is created, and then an instance of the Calculator class is created with that operation instance. Finally, the Calculate method of the Calculator object is called to calculate the result and display the result or an error if division by zero is attempted.


# TMPS_lab_2 - Code in C# where 2 design patterns are used
Main tasks:
    1. Choose an OO programming language and a suitable IDE or Editor (No frameworks/libs/engines allowed).

    2. Select a domain area for the sample project.

    3. Define the main involved classes and think about what instantiation mechanisms are needed.

    4. Based on the previous point, implement at least 2 creational design patterns in your project.

Some Theory:
    Creational design patterns are a category of design patterns that focus on the process of object creation. They provide a way to create objects in a flexible and controlled manner, while decoupling the client code from the specifics of object creation. Creational design patterns address common problems encountered in object creation, such as how to create objects with different initialization parameters, how to create objects based on certain conditions, or how to ensure that only a single instance of an object is created. There are several creational design patterns that have their own strengths and weaknesses. Each of it is best suited for solving specific problems related to object creation. By using creational design patterns, developers can improve the flexibility, maintainability, and scalability of their code.

    Some examples of this kind of design patterns are:

>>Singleton,Builder,Prototype,Object Pooling,Factory Method,Abstract Factory

The code in Lab 2 demonstrates the implementation of two design patterns: Singleton and Observer. Let's analyze each part in more detail:

Singleton Pattern:

The NotificationSystem class contains a private static instance variable and a private constructor. The private constructor ensures that the class can only be instantiated from within the class.
The static GetInstance() method is used to get an instance of the NotificationSystem class. This method checks if the instance does not already exist and, if so, creates and returns it. This ensures that there is only one instance of the NotificationSystem class.
Observer Pattern:

The INotificationObserver interface defines the Update method, which observer classes must implement.
The NotificationObserver class implements the INotificationObserver interface and defines an Update method that displays a message when called.
The NotificationSystem class has a list of observers and methods for attaching, detaching, and notifying observers.
The Attach method adds an observer to the list of observers.
The Detach method removes an observer from the list of observers.
The Notify method loops through the list of observers and calls the Update method of each observer, sending it a message.
In the Main function, we exemplify the use of the code:

We get the singleton instance of the notification system using the GetInstance() method of the NotificationSystem class.
We create two observers (observer1 and observer2) and register them in the notification system using the Attach method.
We call the Notify method of the notification system to send a message to all registered observers.
We unregister observer1 using the Detach method.
We call the Notify method again to send another message to the remaining observer (observer2).
The result displayed in the console will be:
Observer 1 a primit o notificare: Mesaj de test
Observer 2 a primit o notificare: Mesaj de test
Observer 2 a primit o notificare: Mesaj nou

# TMPS_lab_3 - code in C# where patterns are used:Adapter,Bridge.
Main tasks:
1. By creating a new project, or extending your last one (Lab work Nr2), implement at least 2 structural design patterns in your project:

The implemented design pattern should help to perform the tasks involved in your system.
The object creation mechanisms/patterns can now be buried into the functionalities instead of using them into the client.
There should only be one client for the whole system.
    2. Keep your files grouped (into packages/directories) by their responsibilities (an example project structure):

client,domain,factories,builder,models,utilities,data(if applies)
    3. Document your work in a separate markdown file according to the requirements presented below (the structure can be extended of course):
Topic of the laboratory work
Author
Introduction/Theory/Motivation
Implementation & Explanation (you can include code snippets as well)
Indicate the location of the code snippet
Emphasize the main idea and motivate the usage of the pattern
Results/Screenshots/Conclusions

Theoretical background:
    Structural design patterns are a category of design patterns that focus on the composition of classes and objects to form larger structures and systems. They provide a way to organize objects and classes in a way that is both flexible and efficient, while allowing for the reuse and modification of existing code. Structural design patterns address common problems encountered in the composition of classes and objects, such as how to create new objects that inherit functionality from existing objects, how to create objects that share functionality without duplicating code, or how to define relationships between objects in a flexible and extensible way.
    Some examples of from this category of design patterns are:
Adapter,Bridge,Composite,Decorator,Facade,Flyweight,Proxy


Pattern: Adapter
```
// Adapter Pattern
Adaptee adaptee = new Adaptee();
ITarget target = new Adapter(adaptee);
target.Request();
```
In this section, the Adapter pattern is used. We create an instance of the Adaptee class, which represents an existing system with a SpecificRequest method. We then create an instance of the Adapter class that implements the ITarget interface and uses the Adaptee to adapt between the two interfaces. Finally, we call the Request method on the target object.

Pattern: Bridge
```
// Bridge Pattern
IMessageSender emailSender = new EmailSender();
IMessageSender smsSender = new SmsSender();

CompositeMessageSender compositeSender = new CompositeMessageSender();
compositeSender.AddMessageSender(emailSender);
compositeSender.AddMessageSender(smsSender);

compositeSender.SendMessage("Hello, world!");
```
In this section, the Bridge pattern is used. We define the IMessageSender interface and create two classes that implement it: EmailSender and SmsSender. These classes represent concrete implementations of a message sending system. We then create an instance of the CompositeMessageSender class, which implements the IMessageSender interface and can compose multiple IMessageSender objects to send messages collectively. Finally, we add the emailSender and smsSender to the compositeSender and call the SendMessage method on it.

Now, let's provide the explanations in English:

Pattern: Adapter
```
// Adapter Pattern
Adaptee adaptee = new Adaptee();
ITarget target = new Adapter(adaptee);
target.Request();
```
In this section, the Adapter pattern is used. We create an instance of the Adaptee class, which represents an existing system with a specific method (SpecificRequest). We then create an instance of the Adapter class that implements the ITarget interface and uses the Adaptee to adapt between the two interfaces. Finally, we call the Request method on the target object.

Pattern: Bridge
```
// Bridge Pattern
IMessageSender emailSender = new EmailSender();
IMessageSender smsSender = new SmsSender();

CompositeMessageSender compositeSender = new CompositeMessageSender();
compositeSender.AddMessageSender(emailSender);
compositeSender.AddMessageSender(smsSender);

compositeSender.SendMessage("Hello, world!");
```
In this section, the Bridge pattern is used. We define the IMessageSender interface and create two classes that implement it: EmailSender and SmsSender. These classes represent concrete implementations of a message sending system. We then create an instance of the CompositeMessageSender class, which implements the IMessageSender interface and can compose multiple IMessageSender objects to send messages collectively. Finally, we add the emailSender and smsSender to the compositeSender and call the SendMessage method on it.

Please note that the explanation above refers to the usage of the patterns in the given code example. The patterns themselves have broader applications and can be used in different contexts to solve various design problems.








  
