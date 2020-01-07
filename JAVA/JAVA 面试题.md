## JAVA 面试题

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
**JVM** JVM is an acronym for Java Virtual Machine, it is an abstract machine which provides the runtime environment in which java bytecode can be executed. It is a specification. JVMs are available for many hardware and software platforms (so JVM is platform dependent).

**JRE** JRE stands for Java Runtime Environment. It is the implementation of JVM.

**JDK** JDK is an acronym for Java Development Kit. It physically exists. It contains JRE + development tools.

### 6. Explain the Java Exception Hierarchy.
Java Exceptions are hierarchical and inheritance is used for categorizing the different types of exceptions. Throwable is the parent class of Java Exceptions Hierarchy and it has two child objects Throwable – Error
		  - Exceptions - checked
		  			   - runtime exception
Errors are exceptional scenarios which are out of the scope of applications and it’s not possible to anticipate and recover from them, for example, hardware failure, JVM crash or out of memory error

Checked exceptions are exceptional scenarios that we can anticipate in a program and try to recover from it, for example, FileNotFoundException. We should catch this exception and provide a useful message to the user and log it properly for debugging purpose. The exception is the parent class of all the Checked exceptions.

Runtime exceptions are caused by bad programming, for example, trying to retrieve an element from the Array. At first, we should check the length of the array before trying to retrieve the element otherwise it might throw ArrayIndexOutOfBoundException at runtime. RuntimeException is the parent class of all runtime exceptions.

### 7. What is data encapsulation and what’s its significance?

Encapsulation is a concept in Object Oriented Programming for combining properties and methods in a single unit.

Encapsulation helps programmers to follow a modular approach for software development as each object has its own set of methods and variables and serves its functions independent of other objects. Encapsulation also serves data hiding purpose.

### 5. Explain Mutex
### 6. Explain Semaphore
### 7. What happened when compiling and running JAVA code?
### 8. Generic type
### 9. Stack memory VS Heap memory
