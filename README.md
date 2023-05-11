# TMPS_lab_1 - calculator app in c#
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
