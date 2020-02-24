## OOP Interview Question
Object Oriented programming is a programming style which is associated with the concepts like class, object, Inheritance, Encapsulation, Abstraction, Polymorphism.

### Class & Objects
* A class is a collection of method and variables. It is a blueprint that defines the data and behavior of a type.
* An instance/object of class. a class is a template for objects, and an object is an instance of a class.
* Class can have sub-classes, and an object doesn’t have sub-objects.

### Inheritance
Inheritance is a feature of object-oriented programming that allows code reusability when a class includes property of another class. Inheritance enables you to create new classes that re-use, extend and modify the behaviour that is defined in other classes

### Abstraction
Abstraction means, showcasing only the required things to the outside world while hiding the details.(use public private, protected). Abstraction is done when we need to inherit from certain class but do not instantiate the objects of that class.

### Encapsulation
Encapsulation means that we want to hide unnecessary details from the user. Group all relevant things together. I.e. encapsulation is wrapping/binding up of data and member functions in single unit.

### Polymorphism
When an object exhibits different behavior in different situation. Polymorphism is a concept, which allows us to redefine the way something works, by either changing how it is done or by changing the parts used to get it done. This can be done in two ways, overloading and overriding.

- **Overloading** occurs when two or more methods in one class have the same method name but different parameters.
- **Overriding** means having two methods with the same method name and parameters (i.e., method signature). One of the methods is in the parent class and the other is in the child class. Overriding allows a child class to provide a specific implementation of a method that is already provided its parent class.

### Object-oriented programming languages
* JAVA
* JavaScript
* C++
* Python
* PHP
* Scala
* Ruby
* Visual Basic .NET

### What are the access modifiers?
* public - members are accessible from outside the class
* private - members cannot be accessed (or viewed) from outside the class
* protected - members cannot be accessed from outside the class, however, they can be accessed in inherited classes. You will learn more about Inheritance later.
* Friend
* Protected Friend

### Constructor & Destructor
- **Constructor**
It is a method used to initialize the state of an object, and it gets invoked at the time of object creation. Rules forconstructor are:
    * Constructor Name should be same asclass name.
    * Constructor must have no return type.
- **Destructor** 
It is a method which is automatically called when the object ismade ofscope or destroyed. Destructor name is also same asclass name but with the tilde symbol before the name.

### Inline function
**Inline function** is a technique used by the compilers and instructs to insert complete body of the function wherever that function is used in the program source code.

### What is an abstract class?
An **abstract class** is a class which cannot be instantiated. Creation of an object is not possible with abstract class , but it can be inherited. An abstract class can contain only Abstract method. Java allows only abstract method in abstract class while for other language it allows non-abstract method as well.

### What is an interface?
An **interface** is a collection of abstract method. If the class implements an inheritance, and then thereby inherits all the abstract methods of an interface.

### What is exception handling?
Exception is an event that occurs during the execution of a program. Exceptions can be of any type — Run time exception, Error exceptions. Those exceptions are handled properly through exception handling mechanism like try, catch and throw keywords.

### What is the difference between structure and a class?
Structure default access type is public , but class access type is private. A structure is used for grouping data whereas class can be used for grouping data and methods. Structures are exclusively used for data and it doesn’t require strict validation , but classes are used to encapsulates and inherit data which requires strict validation.

### What is a copy constructor?
This is a special constructor for creating a new object as a copy of an existing object. There will be always only on copy constructor that can be either defined by the user or the system.

### What is static and dynamic binding?
Binding is nothing but the association of a name with the class. 
* **Static binding** is a binding in which name can be associated with the class during compilation time , and it is also called as early Binding.
* **Dynamic binding** is a binding in which name can be associated with the class during execution time , and it is also called as Late Binding.
