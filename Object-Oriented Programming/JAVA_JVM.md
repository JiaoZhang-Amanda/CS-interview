* [JVM Run-Time Data Areas](#fireJVM-RunTime-Data-Areas)
* [Garbage Collection](#fireGarbage-Collection)
## :fire:JVM
### What is JVM?
**Java Virtual Machine (JVM)** is a engine that provides runtime environment to drive the Java Code or applications. It converts Java bytecode into machines language. JVM is a part of Java Run Environment (JRE).
### How JVM works?
First, Java code is complied into bytecode. This bytecode gets interpreted on different machines. Between host system and Java source, Bytecode is an intermediary language. JVM is responsible for allocating memory space.
![](https://www.guru99.com/images/java/052016_0614_WorkingofJa10.jpg)
### Explain the difference between JRE, JDK, JVM, and JIT.
* **JRE** is an abbreviation of Java Runtime Environment that consist of sets of files needed by JVM throughout the runtime.
* **JVM** is an abbreviation of Java Virtual Machine which delivers the runtime environment for collected Java Bytecode. JVM is in control of the conversion of the bytecode into machine-readable code.
* **JDK** is an abbreviation for Java Development Kit which contains JRE including development tools for the purpose of development. JDK is required to write and execute a Java code.
* **JIT** is an abbreviation of Just in Time compilation, and this helps to improve the performance of Java application by converting Java bytecode into native code when they cross a certain threshold, i.e. the mostly hot code is transformed into native code.

### What happened when compiling and running JAVA code?
Programs are not compiled into executable file. They are compiled into bytecode, which the JVM executes at runtime.
Java source code is compiled into bytecode when we use javac compiler.
The bytecode gets saved on the disk with the file extension.class when the program is to be run.
The bytecode is converted using the Just-in-time(JIT) compiler.
The result is machine code which is fed to the memory and is executed.


### JVM Architecture
It contains classloader, memory area, execution engine etc.
![](https://segmentfault.com/img/bVkZat)

## :fire:JVM Run-Time Data Areas
* Created per thread– PC register, JVM stack, Native method stack
* Shared by threads– Heap, Method area, Run-time constant pool<br>
![](https://4.bp.blogspot.com/-m1QNXYUo8dg/WriYyHlzeiI/AAAAAAAAAmo/YB1Bzw2a65EvS-hGvS1UczQLNo-dAf_mgCLcBGAs/s1600/JVM%2BData%2BAreas.png)
### Program Counter (PC) Register
In a JVM at any given time many threads may be executing. Each of excuting thread gets its own PC register.

If the method executed by the JVM thread is a JAVA method, the PC register contains the address of the Java Virtual Machine instruction currently being executed. 
### Java Virtual Machine (JVM) stacks
Each JVM threads has its own JVM stack which is created when the thread starts. 
![](https://camo.githubusercontent.com/96d3e63fbdedc3e6af5f8365815898bef9799ea3/68747470733a2f2f63732d6e6f7465732d313235363130393739362e636f732e61702d6775616e677a686f752e6d7971636c6f75642e636f6d2f38343432353139662d306234642d343866342d383232392d3536663938343336336336392e706e67)
* If the computation in a thread requires a larger native method stack than is permitted, the Java Virtual Machine throws a **StackOverflowError**.
* If native method stacks can be dynamically expanded and native method stack expansion is attempted but insufficient memory can be made available, or if insufficient memory can be made available to create the initial native method stack for a new thread, the Java Virtual Machine throws an **OutOfMemoryError**.
### Native method stacks
Native method stacks are allocated per thread when each thread is created.
### Heap Area
* Heap is created on the JVM start-up and shared among all Java Virtual Machine threads.
* Once the object stored on the heap is not having any reference, memory for that object is reclaimed by **garbage collector** which is an automatic storage management system. Objects are never explicitly deallocated.
* If a computation requires more heap than can be made available by the automatic storage management system, the Java Virtual Machine throws an **OutOfMemoryError**.
### Method area
* Method area stores meta data about the loaded classes and interfaces. It stores per-class structures such as the run-time constant pool, field and method data, and the code for methods and constructors.
* If memory in the method area cannot be made available to satisfy an allocation request, the Java Virtual Machine throws an **OutOfMemoryError**.
### Run-Time Constant Pool
* Constant_pool contains constants (string literals, numeric literals) which are known at compile-time, it also stores method and field references that must be resolved at run time.

## :fire:Garbage Collection
### How JAVA garbage collection works? 
Java garbage collection is the process by which Java programs perform automatic memory management. When Java programs run on the JVM, objects are created on the heap, once an object is no longer referenced and therefore is not reachable by the code, the garbage collector finds these unused objects and deletes them to free up memory.
### Is it guarateed to work? 
No, it is not guaranteed to work. If there is insufficient memory remaining to satisfy the amount needed for a new object, the garbage collector will attempt to reclaim as much memory as possible by releasing memory. However, it is possible for a developer to mistakenly create objects which never go out of scope, thus consuming more and more memory until all heap is exhausted.
### Advantage
* It makes java memory efficient because garbage collector removes the unreferenced objects from heap memory.
* It is automatically done by the garbage collector(a part of JVM) so we don't need to make extra efforts.
### How can an object be unreferenced?
1) By nulling a reference:
    Employee e=new Employee();  
    e=null;  
2) By assigning a reference to another:
    Employee e1=new Employee();  
    Employee e2=new Employee();  
    e1=e2;//now the first object referred by e1 is available for garbage collection  
3) By anonymous object:
    new Employee();  
### Methods
1) **finalize()**<br>
`protected void finalize(){}  `<br>
The finalize() method is invoked each time before the object is garbage collected. This method can be used to perform cleanup processing. This method is defined in Object class as:
2) **gc()**<br>
`public static void gc(){}`<br>
The gc() method is used to invoke the garbage collector to perform cleanup processing. The gc() is found in System and Runtime classes.
### Example
```
public class TestGarbage1{  
 public void finalize(){System.out.println("object is garbage collected");}  
 public static void main(String args[]){  
  TestGarbage1 s1=new TestGarbage1();  
  TestGarbage1 s2=new TestGarbage1();  
  s1=null;  
  s2=null;  
  System.gc();  
 }  
}  
```
Output:
```
object is garbage collected
object is garbage collected
```
