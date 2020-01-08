## JAVA Interview Question

### 1. Does JAVA has destructor? How to force it?
No. Because Java is a garbage collected language. You can not predict when an object will be destroyed. 

### 2. How JAVA garbage collection works? Is it guarateed to work?
Java garbage collection is the process by which Java programs perform automatic memory management. When Java programs run on the JVM, objects are created on the heap, once an object is no longer referenced and therefore is not reachable by the code, the garbage collector finds these unused objects and deletes them to free up memory.
No, it is not guaranteed to work. If there is insufficient memory remaining to satisfy the amount needed for a new object, the garbage collector will attempt to reclaim as much memory as possible by releasing memory. However, it is possible for a developer to mistakenly create objects which never go out of scope, thus consuming more and more memory until all heap is exhausted.

### 3. "==" VS "equals()"
- The two operators are used to compare objects to check equality.
- "==" for address comparison; "equals()" for content comparison. == checks if both objects point to the same memory location whereas .equals() evaluates to the comparison of values in the objects.

### 4. HashTable VS HashMap
- HashTable is synchronized and thread-safe(can be shared with many threads), whereas HashMap is not and not-thread safe(can not be shared). Thus, HashMap is better for non-threaded applications.(HashMap can be synchronized by Map m = Collections.synchronizeMap(hashMap))
- HashTable does not allow null keys or values, HashMap allows one null key and any number of null values.

### 5. Does Java support multiple inheritance?
No, you can only extend a single class but you can implement multiple interfaces.

### 6. What is difference between JDK,JRE and JVM?
**JVM** is an acronym for Java Virtual Machine, it is an abstract machine which provides the runtime environment in which java bytecode can be executed. It is a specification. JVMs are available for many hardware and software platforms (so JVM is platform dependent).

**JRE** stands for Java Runtime Environment. It is the implementation of JVM.

**JDK** is an acronym for Java Development Kit. It physically exists. It contains JRE + development tools.

### 7. Explain the Java Exception Hierarchy.
Java Exceptions are hierarchical and inheritance is used for categorizing the different types of exceptions. Throwable is the parent class of Java Exceptions Hierarchy and it has two child objects 
Throwable: Error & Exceptions
Exceptions: checked & runtime exception

**Errors** are exceptional scenarios which are out of the scope of applications and it’s not possible to anticipate and recover from them, for example, hardware failure, JVM crash or out of memory error

**Checked exceptions** are exceptional scenarios that we can anticipate in a program and try to recover from it, for example, FileNotFoundException. We should catch this exception and provide a useful message to the user and log it properly for debugging purpose. 

**Runtime exceptions** are caused by bad programming, for example, trying to retrieve an element from the Array. At first, we should check the length of the array before trying to retrieve the element otherwise it might throw ArrayIndexOutOfBoundException at runtime.

### 8. What is data encapsulation and what’s its significance?

**Encapsulation** is a concept in Object Oriented Programming for combining properties and methods in a single unit. Encapsulation helps programmers to follow a modular approach for software development as each object has its own set of methods and variables and serves its functions independent of other objects. Encapsulation also serves data hiding purpose.

### 9. Explain Mutex
We use mutex to protect critical section and thus prevent race condition. Each time only one process will be able to have the key and proceed with their work. Mutex has a boolean variable and indicates if the lock is available. A process that attempts to acquire an unavailable lock is blocked until the lock is released. It is locking mechanism.

### 10. Explain Semaphore
A semaphore S is a variable. It is signaling mechanism. wait() & signal()

### 11. What happened when compiling and running JAVA code?
Programs are not compiled into executable file. They are compiled into bytecode, which the JVM executes at runtime.
Java source code is compiled into bytecode when we use javac compiler.
The bytecode gets saved on the disk with the file extension.class when the program is to be run.
The bytecode is converted using the Just-in-time(JIT) compiler.
The result is machine code which is fed to the memory and is executed.

### 12. String VS StringBuffer VS StringBuiler
- String is immutable, whereas StringBuffer and StringBuider are mutable classes.
  whenever we do String manipulation like concatenation, substring etc, it generates a new String and discards the older String for garbage collection.
- StringBuffer is thread safe and synchronized whereas StringBuilder is not.
  StringBuilder is more faster than StringBuffer. StringBuffer provides Thread safety but on a performance cost. StringBuffer: all of its public methods are synchronized


### 13. Stack memory VS Heap memory
- Stack memory is used to store local variables and function call while heap memory is used to store objects in Java
- Stack is used for static memory allocation and Heap for dynamic memory allocation, both stored in the computer's RAM.
- Stack frame access is easier than the heap frame as the stack have small region of memory and is cache friendly, but in case of heap frames which are dispersed throughout the memory so it cause more cache misses.

### 14. final VS finalize VS finally
- Final is a keyword. Final is used to apply restrictions on class, method and variable. Final class can't be inherited, final method can't be overridden and final variable value can't be changed.
- Finally is a block. Finally is used to place important code, it will be executed whether exception is handled or not.
- Finalize is a method. Finalize is used to perform clean up processing just before object is garbage collected.

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

### 16. Overriding VS Overloading
Overloading occurs when two or more methods in one class have the same method name but different parameters.
Overriding means having two methods with the same method name and parameters (i.e., method signature). One of the methods is in the parent class and the other is in the child class. Overriding allows a child class to provide a specific implementation of a method that is already provided its parent class.

### 17. List VS Set VS Map
Set: HashSet, LinkedHashSet, TreeSet
List: ArrayList, LinkedList, Vector
Map: HashMap, LinkedHashMap, HashTable, TreeMap

- List allows duplicates while Set doesn't allow duplicates.
- Map holds two objects per Entry e.g. a key and a value and It may contain duplicate values but keys are always unique.
- List is an ordered collection, List's contract maintains insertion order or element. Set is an unordered collection, you get no guarantee on which order element will be stored. 
- The list allows null elements and you can have many null objects in a List because it also allowed duplicates. Set just allow one null element as there is no duplicate permitted while in Map you can have null values and at most one null key. 

### 18. Serialization VS Deserialization
Serialization is a mechanism of converting the state of an object into a byte stream. Deserialization is the reverse process where the byte stream is used to recreate the actual Java object in memory.

### 19. What are the object-oriented features of java?
abstraction, encapsulation, inheritance, and polymorphism.
**Abstraction**: simple things like objects, classes, and variables represent more complex underlying code and data. 
**Encapsulation**: It’s a protective barrier that keeps the data and code safe within the class itself. This way, we can re-use objects like code components or variables without allowing open access to the data system-wide.
**Inheritance**: It lets programmers create new classes that share some of the attributes of existing classes. 
**Polymorphism**: use the same word to mean different things in different contexts. method overloading & method overriding.

### 10. what is contract between hashcode and equals method in java?
public boolean equals(Object obj)
public int hashCode()
- If two objects are equal, then they must have the same hash code.
- If two objects have the same hash code, they may or may not be equal.

### 21. ArrayList VS Vector VS LinkedList
- ArrayList is non-synchronized, while Vector is synchronized which means multiple threads can work on ArrayList at the same time.
- ArrayList grow by half of its size when resized while Vector doubles the size of itself by default when grows.
- ArrayList gives better performance as it is non-synchronized. Vector operations gives poor performance as they are thread-safe.
- LinkedList is faster in add and remove, but slower in get.
