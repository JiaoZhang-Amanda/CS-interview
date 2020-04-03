## JAVA Interview Question
* [JAVA Basic Concept](#JAVA-Basic-Concept)
    * [OOP](#oop)
    * [JVM](#jvm)
    * [Modifiers](#Modifiers)
    * [Multithreading](#Multithreading)
    * [Inner Classes](#Inner-Classes)
* [JAVA Methods](#JAVA-Methods)
    * [String VS StringBuffer VS StringBuiler](#String-VS-StringBuffer-VS-StringBuiler)
    * ["==" VS "equals()"](#==-VS-equals())
    * [final VS finalize VS finally](#final-VS-finalize-VS-finally)
    * [List VS Set VS Map](#List-VS-Set-VS-Map)
    * [ArrayList VS Vector VS LinkedList](#ArrayList-VS-Vector-VS-LinkedList)
    * [what is contract between hashcode and equals method in java?](#what-is-contract-between-hashcode-and-equals-method-in-java?)
## JAVA Basic Concept
### OOP
* **Inheritance**: It lets programmers create new classes that share some of the attributes of existing classes. 
* **Poymorphism**: uses those methods to perform different tasks when you inherit attributes and methods from another class. method overloading & method overriding.
    * **Overloading** occurs when two or more methods in one class have the same method name but different parameters.
    * **Overriding** means having two methods with the same method name and parameters (i.e., method signature). One of the methods is in the parent class and the other is in the child class. Overriding allows a child class to provide a specific implementation of a method that is already provided its parent class.
* **Encapsulation**: to make sure that "sensitive" data is hidden from users. To achieve this, you must:
    * declare class variables/attributes as private
    * provide public get and set methods to access and update the value of a private variable
* **Abstraction**: Data abstraction is the process of hiding certain details and showing only essential information to the user.
    Abstraction can be achieved with either **abstract classes** or **interfaces**

#### 1). Does Java support multiple inheritance?
No, you can only extend a single class but you can implement multiple interfaces.
#### 2) What is data encapsulation and what’s its significance?
**Encapsulation** is a concept in Object Oriented Programming for combining properties and methods in a single unit. Encapsulation helps programmers to follow a modular approach for software development as each object has its own set of methods and variables and serves its functions independent of other objects. Encapsulation also serves data hiding purpose.

### JVM
#### 1) Explain the difference between JRE, JDK, JVM, and JIT.
* **JRE** is an abbreviation of Java Runtime Environment that consist of sets of files needed by JVM throughout the runtime.
* **JVM** is an abbreviation of Java Virtual Machine which delivers the runtime environment for collected Java Bytecode. JVM is in control of the conversion of the bytecode into machine-readable code.
* **JDK** is an abbreviation for Java Development Kit which contains JRE including development tools for the purpose of development. JDK is required to write and execute a Java code.
* **JIT** is an abbreviation of Just in Time compilation, and this helps to improve the performance of Java application by converting Java bytecode into native code when they cross a certain threshold, i.e. the mostly hot code is transformed into native code.

### Modifiers
* The access modifiers in Java specifies the accessibility or scope of a field, method, constructor, or class. We can change the access level of fields, constructors, methods, and class by applying the access modifier on it.
* **Types of modifiers**
    * **access modifiers**: controls the access level
    * **non-access modifiers**: do not control access level, but provides other functionality
* **Types of Java access modifiers**
    * **Private**: The access level of a private modifier is only within the class. It cannot be accessed from outside the class.
    * **Default**: The access level of a default modifier is only within the package. It cannot be accessed from outside the package. If you do not specify any access level, it will be the default.
    * **Protected**: The access level of a protected modifier is within the package and outside the package through child class. If you do not make the child class, it cannot be accessed from outside the package.
    * **Public**: The access level of a public modifier is everywhere. It can be accessed from within the class, outside the class, within the package and outside the package.
    
    Access Modifier    |within class  |  within package  |  outside package by subclass only   | outside package
    --|--|--|--|--
    Private  |  Y |   N  |  N |   N
    Default   | Y  |  Y |   N  |  N
    Protected |   Y   | Y    |Y|    N
    Public   | Y |   Y    |Y    |Y
* **Non-Access Modifiers**
* For classes, you can use either final or abstract:
    * **final**: The class cannot be inherited by other classes
    * **abstract**: The class cannot be used to create objects(To access an abstract class, it must be inherited from another class. )
* For attributes and methods: 
    * **final**: Attributes and methods cannot be overridden/modified(If you don't want the ability to override existing attribute values, declare attributes as final)
    * **static** :  Attributes and methods belongs to the class, rather than an object. Static methods can be called without creating objects
    * **abstract**: Can only be used in an abstract class, and can only be used on methods. The method does not have a body, for example abstract void run();. The body is provided by the subclass (inherited from). 
    * **transient**: Attributes and methods are skipped when serializing the object containing them
    * **synchronized**: Methods can only be accessed by one thread at a time
    * **volatile**: The value of an attribute is not cached thread-locally, and is always read from the "main memory"

### Multithreading
### 1) Life cycle of thread
![](https://www.tutorialspoint.com/java/images/Thread_Life_Cycle.jpg)
* New − A new thread begins its life cycle in the new state. It remains in this state until the program starts the thread. It is also referred to as a born thread.
* Runnable − After a newly born thread is started, the thread becomes runnable. A thread in this state is considered to be executing its task.
* Waiting − Sometimes, a thread transitions to the waiting state while the thread waits for another thread to perform a task. A thread transitions back to the runnable state only when another thread signals the waiting thread to continue executing.
* Timed Waiting − A runnable thread can enter the timed waiting state for a specified interval of time. A thread in this state transitions back to the runnable state when that time interval expires or when the event it is waiting for occurs.
* Terminated (Dead) − A runnable thread enters the terminated state when it completes its task or otherwise terminates.

### 2) Explain Mutex
We use mutex to protect critical section and thus prevent race condition. Each time only one process will be able to have the key and proceed with their work. Mutex has a boolean variable and indicates if the lock is available. A process that attempts to acquire an unavailable lock is blocked until the lock is released. It is locking mechanism.

### 3) Explain Semaphore
A semaphore S is a variable. It is signaling mechanism. wait() & signal()

### Inner Classes
* In Java, it is also possible to nest classes (a class within a class). The purpose of nested classes is to group classes that belong together, which makes your code more readable and maintainable.
* To access the inner class, create an object of the outer class, and then create an object of the inner class:
```
class OuterClass {
  int x = 10;

  class InnerClass {
    int y = 5;
  }
}

public class MyMainClass {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}

```
* Unlike a "regular" class, an inner class can be **private or protected**. If you don't want outside objects to access the inner class, declare the class as private
* An inner class can also be **static**, which means that you can access it without creating an object of the outer class
* One advantage of inner classes, is that they can access attributes and methods of the outer class

## JAVA Methods
### String VS StringBuffer VS StringBuiler
- String is immutable, whereas StringBuffer and StringBuider are mutable classes.
  whenever we do String manipulation like concatenation, substring etc, it generates a new String and discards the older String for garbage collection.
- StringBuffer is thread safe and synchronized whereas StringBuilder is not.
  StringBuilder is more faster than StringBuffer. StringBuffer provides Thread safety but on a performance cost. StringBuffer: all of its public methods are synchronized
  
### "==" VS "equals()"
  - The two operators are used to compare objects to check equality.
  - "==" for address comparison; "equals()" for content comparison. == checks if both objects point to the same memory location whereas .equals() evaluates to the comparison of values in the objects.

### final VS finalize VS finally
- Final is a keyword. Final is used to apply restrictions on class, method and variable. Final class can't be inherited, final method can't be overridden and final variable value can't be changed.
- Finally is a block. Finally is used to place important code, it will be executed whether exception is handled or not.
- Finalize is a method. Finalize is used to perform clean up processing just before object is garbage collected.


### what is contract between hashcode and equals method in java?
public boolean equals(Object obj)
public int hashCode()
- If two objects are equal, then they must have the same hash code.
- If two objects have the same hash code, they may or may not be equal.

____
### 1. Does JAVA has destructor? How to force it?
No. Because Java is a garbage collected language. You can not predict when an object will be destroyed. 

### 7. Explain the Java Exception Hierarchy.
Java Exceptions are hierarchical and inheritance is used for categorizing the different types of exceptions. Throwable is the parent class of Java Exceptions Hierarchy and it has two child objects 
Throwable: Error & Exceptions
Exceptions: checked & runtime exception

**Errors** are exceptional scenarios which are out of the scope of applications and it’s not possible to anticipate and recover from them, for example, hardware failure, JVM crash or out of memory error

**Checked exceptions** are exceptional scenarios that we can anticipate in a program and try to recover from it, for example, FileNotFoundException. We should catch this exception and provide a useful message to the user and log it properly for debugging purpose. 

**Runtime exceptions** are caused by bad programming, for example, trying to retrieve an element from the Array. At first, we should check the length of the array before trying to retrieve the element otherwise it might throw ArrayIndexOutOfBoundException at runtime.


### 11. What happened when compiling and running JAVA code?
Programs are not compiled into executable file. They are compiled into bytecode, which the JVM executes at runtime.
Java source code is compiled into bytecode when we use javac compiler.
The bytecode gets saved on the disk with the file extension.class when the program is to be run.
The bytecode is converted using the Just-in-time(JIT) compiler.
The result is machine code which is fed to the memory and is executed.

### 13. Stack memory VS Heap memory
- Stack memory is used to store local variables and function call while heap memory is used to store objects in Java
- Stack is used for static memory allocation and Heap for dynamic memory allocation, both stored in the computer's RAM.
- Stack frame access is easier than the heap frame as the stack have small region of memory and is cache friendly, but in case of heap frames which are dispersed throughout the memory so it cause more cache misses.


### 15. Boxing and Unboxing
Autoboxing is the automatic conversion that the Java compiler makes between the primitive types and their corresponding object wrapper classes. For example, converting an int to an Integer, a double to a Double, and so on. If the conversion goes the other way, this is called unboxing.

|Primitive type|Wrapper class|
|--|--|
|boolean|Boolean|
|byte	| Byte|
|char	 |Character|
|float	 |Float|
|int	     |Integer|
|long	|Long|
|short	|Short|
|double	|Double|



### 18. Serialization VS Deserialization
Serialization is a mechanism of converting the state of an object into a byte stream. Deserialization is the reverse process where the byte stream is used to recreate the actual Java object in memory.
