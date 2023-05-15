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

Singleton

Builder

Prototype

Object Pooling

Factory Method

Abstract Factory

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
