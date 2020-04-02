* [Data Type](#firedata-type)
    * [Primitive Type](#Primitive-type)
    * [Wrapper Classes](#Wrapper-Classes)
    * [Buffer Pool](#Buffer-Pool)
* [String](#fireString)
    * [Principle -- Why Immutable?](#principle----why-immutable)
    * [Immutable Benefits](#Immutable-Benefits)
    * [String VS StringBuffer VS StringBuiler](#string-stringbuffer-and-stringbuilder)
* [Operation](#fireoperation)
    * [“pass-by-reference” & “pass-by-value”](#pass-by-reference--pass-by-value)
    * [Type Casting](#Type-casting)
* [Keyword](#firekeyword)
    * [final](#final)
    * [static](#static)
* [Object Methods](#fireobject-methods)
    * [equals()](#equals)
    * [hashCode()](#hashCode)
    * [toString()](#toString)
    * [clone()](#clone)
* [Inheritance](#fireInheritance)
    * [Modifiers](#Modifiers)
    * [Abstraction Class & Interface](#Abstraction-Class--Interface)
    * [Super](#super)
    * [Override & Overload](#Override--Overload)
* [Container Type](#fireContainer-Type)
    * [Collection](#Collection)
    * [Map](#Map)
* [Exception](#fireException)
* [Generics](#fireGenerics)
* [JRE or JDK](#fireJRE-or-JDK)
## :fire:Data Type
### Primitive Type
Data Type|    Default Value (for fields)|size
--|--|--
byte   |  0|8
short  |   0|16
int |    0|32
long |    0L|64
float  |   0.0f|32
double   |  0.0d|64
char   |  '\u0000'|16
boolean |    false|-
* The JVM converts Boolean to int at compile time
* Primitive types can never be null.

### Wrapper Classes
A wrapper class is an object that encapsulates a primitive type.
* **Autoboxing**: automatic conversion of primitive types to their corresponding object wrapper classes. e.g. int -> Integer
* **Unboxing**: automatic conversion of object wrapper types into their corresponding primitive types. e.g. Integer -> int
![](https://media.geeksforgeeks.org/wp-content/uploads/Wrapper.png)
* Each wrapper class has Ocbject as a superclass. Byte, Short, Integer, Long Float and Double have Number as their direct superclass. This means that each wrapper class can implement the methods of the Object class such as hashCode(), equals(Object obj), clone(), and toString().<br>
![](https://miro.medium.com/max/1090/1*AQzGbqmrJfVMJeJ7UVQctw.png)

### Buffer Pool
* `new Integer(123)`: create a new object
* `Integer.valueOf(123)`: return the object from buffer pool. Multiple calls get a reference to the **same** object.
```JAVA
Integer x = new Integer(123);
Integer y = new Integer(123);
System.out.println(x == y);    // false
Integer z = Integer.valueOf(123);
Integer k = Integer.valueOf(123);
System.out.println(z == k);   // true
```
* When arguments on both sides of the “==” operator are objects, no unboxing will occur and the “==” operator will compare the **object’s reference** in memory.
* "==" between The wrapper type and the primitive type: automatically converts the wrapper type to the primitive type, and then compares the values `new Integer（123）==123 //true`
```JAVA
Integer m = 123;
Integer n = 123;
System.out.println(m == n); // true
```
* The compiler calls the valueOf() method during autoboxing, so multiple instances of an Integer with the same value and the value within the cache pool are created using autoboxing, and the same object is referenced.

## :fire:String
### Principle -- Why Immutable?
* String is declared final, so it cannot be inherited. (wrapper classes such as Integer cannot be inherited)
* Java8
```JAVA
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {
    /** The value is used for character storage. */
    private final char value[];
}
```
* Java9
```JAVA
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {
    /** The value is used for character storage. */
    private final byte[] value;

    /** The identifier of the encoding used to encode the bytes in {@code value}. */
    private final byte coder;
}
```
* The value array is declared final, which means that after the value array has been initialized, it cannot refer to any other array. And there is no way to change the value array inside String, so you can guarantee that String is **immutable**.
* String constructor source code
```JAVA
public String(String original) {
    this.value = original.value;
    this.hash = original.hash;
}
```
### Immutable Benefits
1) **String Pool**
    * Caching the String literals and reusing them saves a lot of heap space because different String variables refer to the same object in the String pool. **String intern pool** serves exactly this purpose.
![](https://www.baeldung.com/wp-content/uploads/2018/08/Why_String_Is_Immutable_In_Java.jpg)
    * Because of the presence of the String pool in the preceding example, two different variables are pointing to same String object from the pool, thus **saving crucial memory resource**.
    * String pool exists because Strings are immutable.
    * When a String calls the **intern()** method, a reference to the String Pool is returned if there is already a String in the String Pool that is equal to the value of the String (using the equals() method). Otherwise, a new String is added to the String Pool and a reference to the new String is returned.
    * If you create a String as a literal like "BBB", you automatically drop the String into a String Pool.
```JAVA
String s1 = new String("aaa");
String s2 = new String("aaa");
System.out.println(s1 == s2);           // false
String s3 = s1.intern();
String s4 = s1.intern();
System.out.println(s3 == s4);           // true
String s5 = "bbb";
String s6 = "bbb";
System.out.println(s5 == s6);  // true
```
2) **Security**
    * The String is widely used in Java applications to store sensitive pieces of information like usernames, passwords, connection URLs, network connections, etc. It's also used extensively by JVM class loaders while loading classes.
3) **Synchronization**
    * Being immutable automatically makes the String thread safe since they won't be changed when accessed from multiple threads.
4) **Hashcode Caching**
    * Since String objects are abundantly used as a data structure, they are also widely used in hash implementations like HashMap, HashTable, HashSet, etc. When operating upon these hash implementations, hashCode() method is called quite frequently for bucketing.
    * The immutability guarantees Strings that their value won’t change. So the hashCode() method is overridden in String class to facilitate caching, such that the hash is calculated and cached during the first hashCode() call and the same value is returned ever since.
    * This, in turn, improves the performance of collections that uses hash implementations when operated with String objects.
5) **Performance**
    * It enhances the performance by saving heap memory and faster access of hash implementations when operated with Strings.
### String, StringBuffer and StringBuilder
- **Immutable**
    * String is immutable, whereas StringBuffer and StringBuider are mutable classes.
    * whenever we do String manipulation like concatenation, substring etc, it generates a new String and discards the older String for garbage collection.
- **Thread Safe**
    * String is immutable, so it is thread-safe
    * StringBuffer is thread safe and synchronized. Synchronized is used internally for synchronization. StringBuffer provides Thread safety but on a performance cost. StringBuffer: all of its public methods are synchronized
    * StringBuilder is not thread safe. StringBuilder is more faster than StringBuffer. 

## :fire:Operation
###  “pass-by-reference” & “pass-by-value”
* Java is always **pass-by-value**. But, when we pass the value of an object, we are passing the reference to it.
```JAVA
public static void main(String[] args) {
    Dog aDog = new Dog("Max");
    Dog oldDog = aDog;

    // we pass the object to foo
    foo(aDog);
    // aDog variable is still pointing to the "Max" dog when foo(...) returns
    aDog.getName().equals("Max"); // true
    aDog.getName().equals("Fifi"); // false
    aDog == oldDog; // true
}

public static void foo(Dog d) {
    d.getName().equals("Max"); // true
    // change d inside of foo() to point to a new Dog instance "Fifi"
    d = new Dog("Fifi");
    d.getName().equals("Fifi"); // true
}
```
* The value aDog within main is not changed in the function foo with the Dog "Fifi" as the object reference is passed by value.
```JAVA
public static void main(String[] args) {
    Dog aDog = new Dog("Max");
    Dog oldDog = aDog;

    foo(aDog);
    // when foo(...) returns, the name of the dog has been changed to "Fifi"
    aDog.getName().equals("Fifi"); // true
    // but it is still the same dog:
    aDog == oldDog; // true
}

public static void foo(Dog d) {
    d.getName().equals("Max"); // true
    // this changes the name of d to be "Fifi"
    d.setName("Fifi");
}
```
* Any operations that foo performs on d are such that, for all practical purposes, they are performed on aDog, but it is not possible to change the value of the variable aDog itself.

### Type Casting
* **Type casting** is when you assign a value of one primitive data type to another type.
    * Widening Casting (automatically) - converting a smaller type to a larger type size
`byte -> short -> char -> int -> long -> float -> double`
    * Narrowing Casting (manually) - converting a larger type to a smaller size type
`double -> float -> long -> int -> char -> short -> byte`
```JAVA
int myInt = 9;
double myDouble = myInt; // Automatic casting: int to double
double myDouble = 9.78;
int myInt = (int) myDouble; // Manual casting: double to int
```
* **Implicit Type Conversion**
    * Java's +=, -=, *=, /= compound assignment operators doesn't require casting
    * Using the += or ++ operator performs implicit type conversions.
```JAVA
short s1 = 1;
s1 += 1;
s1++; //==> s1 = (short) (s1 + 1);
byte b = 10;
b *= 5.7;
System.out.println(b); // prints 57
byte b = 100;
b /= 2.5;
System.out.println(b); // prints 40
```
* **float & double**: `float f = 1.1f;` 1.1f is the literal of the type float but the 1.1 is the literal of the type double. `float f = 1.1;` is wrong.
* **Switch** statement data type can not be long: Switch does not support long because switch is designed to judge the equivalence of types with only a few values. If the value is too complex, it is better to use if.

## :fire:Keyword
### final
1. Variable
    * For basic types, `final` keeps the value constant;
    * For reference types, `final` leaves the reference unchanged, and no other object can be referenced, but the referenced object itself can be modified.
```JAVA
final int x = 1;
// x = 2;  // cannot assign value to final variable 'x'
final A y = new A();
y.a = 1;
```
2. Methods
    * `final` methods cannot be overridden
    * The private method is implicitly specified as final. If the method in the subclass is signed the same as a private method in the base class, the subclass method does not override the base class method, but defines a new method in the subclass.
3. Class
    * `final` class cannot be inherited by other classes
    
### static
1. **Variable**
* Static variable: also known as a class variable. The variable belongs to the class, all instances of the class share the static variable, can be accessed directly through the class name. Static variables exist in memory only **once**.
```JAVA
private int x;         // 实例变量
private static int y;  // 静态变量

public static void main(String[] args) {
    // int x = A.x;  // Non-static field 'x' cannot be referenced from a static context
    A a = new A();
    int x = a.x;
    int y = A.y;
}
```
2. **Method**
* Attributes and methods belongs to the class, rather than an object. Static methods can be called without creating objects
* A static method must have an implementation, which means it cannot be an abstract method
* You can only access the static fields and static methods of the class belong to, and you cannot have the `this` and `super` keywords in your methods, so they are associated with specific objects.
```JAVA
public class A {

    private static int x;
    private int y;

    public static void func1(){
        int a = x;
        // int b = y;  // Non-static field 'y' cannot be referenced from a static context
        // int b = this.y;     // 'A.this' cannot be referenced from a static context
    }
    // public abstract static void func2();  // Illegal combination of modifiers: 'abstract' and 'static'
}
```
3. **Statement block**
* The static statement block runs once during class initialization.
```JAVA
public class A {
    static {
        System.out.println("123");
    }

    public static void main(String[] args) {
        A a1 = new A();
        A a2 = new A();
    }
}
//output 123
```
4. **Inner Class**
* A non-static inner class depends on an instance of an external class, which means that you need to create an instance of an external class before you can use it to create a non-static inner class. Static inner classes do not.
* Static inner classes cannot access non-static variables and methods of external classes.
```JAVA
public class OuterClass {

    class InnerClass {
    }

    static class StaticInnerClass {
    }

    public static void main(String[] args) {
        // InnerClass innerClass = new InnerClass(); // 'OuterClass.this' cannot be referenced from a static context
        OuterClass outerClass = new OuterClass();
        InnerClass innerClass = outerClass.new InnerClass();
        StaticInnerClass staticInnerClass = new StaticInnerClass();
    }
}
```
5. **package**
* Eliminates the need to specify classnames, simplifying the code but making it much less readable. `import static com.xxx.ClassName.*`
6. **Others**: initial order
* Static variables and static statement blocks take precedence over instance variables and normal statement blocks
* The order in which static variables and static statement blocks are initialized depends on the order in which they are placed in the code.
* superclass(Static variables, static statement blocks)->subclass(Static variables, static statement blocks) -> superclass(instance variable, statement blocks) -> superclass(constructor) -> subclass(instance variable, statement blocks) -> subclass(constructor)
<br>`public static String staticField = "Static variables";`
<br>`static {System.out.println("static statement blocks");}`
<br>`public String field = "instance variable";{System.out.println("statement blocks");}`
<br>`public InitialOrderTest() {System.out.println("constructor");}`

## :fire:Object Methods
### equals()
`public boolean equals(Object obj)`
```JAVA
x.equals(x); // true
x.equals(y) == y.equals(x); // true
x.equals(null); // false;
```
* For primitive types, `==` determines if two values are equal, and there is no equals() method for primitive types.
* For reference types, `==` determines whether two variables refer to the same object, and equals() determines whether the referenced object is equivalent.
```JAVA
Integer x = new Integer(1);
Integer y = new Integer(1);
System.out.println(x.equals(y)); // true
System.out.println(x == y);      // false
```
### hashCode()
`public native int hashCode()`
### toString()
`public String toString()`
The default returns the form tostringexample@4554617c, where the value after @ is the unsigned hexadecimal representation of the hash code.
### clone()
`protected native Object clone() throws CloneNotSupportedException`
* It will throw CloneNotSupportedException when a class does not implement the **Cloneable interface** and call clone () method
* **Shallow Clone**: The copy object and the original object refer to the same object.
* **Deep Clone**: The copy object and the original object refer to the different object.

## :fire:Inheritance
* Java does not support multiple inheritance and can only achieve the same goal by implementing multiple interfaces
### Modifiers
* The access modifiers in Java specifies the accessibility or scope of a field, method, constructor, or class. We can change the access level of fields, constructors, methods, and class by applying the access modifier on it.
* **Types of modifiers**
    * **Access modifiers**: controls the access level
    * **Non-access modifiers**: do not control access level, but provides other functionality
* **Access Modifiers**
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
        
### Abstraction Class & Interface
1)  **Abstraction Class**
* If a class contains abstract methods, the class must be declared an abstract class.
* Abstract classes cannot be instantiated, they can only be inherited
```JAVA
public abstract class AbstractClassExample {

    protected int x;
    private int y;

    public abstract void func1();

    public void func2() {
        System.out.println("func2");
    }
}
public class AbstractExtendClassExample extends AbstractClassExample {
    @Override
    public void func1() {
        System.out.println("func1");
    }
}
```
2) **Interface**
* The members of the interface (field + method) are public by default and are not allowed to be defined as private or protected.
* Interface fields are static and final by default.
```JAVA
public interface InterfaceExample {

    void func1();

    default void func2(){
        System.out.println("func2");
    }

    int x = 123;
    // int y;               // Variable 'y' might not have been initialized
    public int z = 0;       // Modifier 'public' is redundant for interface fields
    // private int k = 0;   // Modifier 'private' not allowed here
    // protected int l = 0; // Modifier 'protected' not allowed here
    // private void fun3(); // Modifier 'private' not allowed here
}
public class InterfaceImplementExample implements InterfaceExample {
    @Override
    public void func1() {
        System.out.println("func1");
    }
}
```
### Super
* You can use the super() function to access the constructor of the super class.
* If a subclass overrides a method of a parent class, you can refer to the method implementation of the parent class by using the super keyword.
```JAVA
public class SuperExample {

    protected int x;
    protected int y;

    public SuperExample(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public void func() {
        System.out.println("SuperExample.func()");
    }
}
public class SuperExtendExample extends SuperExample {

    private int z;

    public SuperExtendExample(int x, int y, int z) {
        super(x, y);
        this.z = z;
    }

    @Override
    public void func() {
        super.func();
        System.out.println("SuperExtendExample.func()");
    }
}
```
### Override & Overload
* **Overloading** occurs when two or more methods in one class have the same method name but different parameters.
* **Overriding** means having two methods with the same method name and parameters (i.e., method signature). One of the methods is in the parent class and the other is in the child class. Overriding allows a child class to provide a specific implementation of a method that is already provided its parent class.
```
/*
    A
    |
    B
    |
    C
    |
    D
 */


class A {

    public void show(A obj) {
        System.out.println("A.show(A)");
    }

    public void show(C obj) {
        System.out.println("A.show(C)");
    }
}

class B extends A {

    @Override
    public void show(A obj) {
        System.out.println("B.show(A)");
    }
}

class C extends B {
}

class D extends C {
}
```
## :fire:Container Type
* The Collection interface and Map interface are the two main “root” interfaces of Java collection classes.
### Collection 
`java.util.Collection`
![](./photo/Collection.png)
* **Set** : Doesn't allow duplicates and unordered collection. Set just allow one null element as there is no duplicate permitted
    * **HashSet**: Hashing based. Search O(1)
    * **TreeSet**: Balanced BST based. TreeSet implements SortedSet. Search O(logn)
    * **LinkedHashSet**
* **List** : Can contain duplicates and elements are ordered. List's contract maintains insertion order or element. The list allows null elements and you can have many null objects in a List.
    * **ArrayList**: Dynamic array based. **Non-synchronized**, multiple threads can work on ArrayList at the same time.
        * `public class ArrayList<E> extends AbstractList<E>
        implements List<E>, RandomAccess, Cloneable, java.io.Serializable`
        * The default size of the array is 10
    * **LinkedList**: Linked list based. A linked list is a sequence of nodes in which each node is connected to the node following it. This forms a chain-like link for data storage. LinkedList can be used as a stack, queue, and dequeue. LinkedList is faster in add and remove, but slower in get.
    * **Vector**: similar with ArrayList but it is **synchronized and thread-safe**. ArrayList grow by half of its size when resized while Vector doubles the size of itself by default when grows.
* **Queue** : Typically order elements in FIFO order
    * **PriorityQueue**: Based on the heap structure.
* **Deque** : Elements can be inserted and removed at both ends. Allows both LIFO and FIFO. 

### Map
`java.util.Map`
![](https://camo.githubusercontent.com/cd126ae7572489beead8b33f3a26a5a0bb1f288e/68747470733a2f2f63732d6e6f7465732d313235363130393739362e636f732e61702d6775616e677a686f752e6d7971636c6f75642e636f6d2f696d6167652d32303139313230383232343735373835352e706e67)
* **HashTable**: **Synchronized and thread-safe**(can be shared with many threads). HashTable does not allow null keys or values
* **HashMap**: Hashing based. HashMap data structure contains Key-Value pairs. All the keys in a HashMap data structure are unique. The values are not necessarily be unique. Different keys may correspond to same value. **Non-synchronized and not thread-safe**. HashMap allows **one null key** and any number of null values.
    * **LinkedHashMap**
* **TreeMap**: TreeMap implements SortedMap.  
* **LinkedHashMap**

## :fire:Exception
Java Exceptions are hierarchical and inheritance is used for categorizing the different types of exceptions. Throwable is the parent class of Java Exceptions Hierarchy and it has two child objects 
- Throwable: Error & Exceptions
- Exceptions: checked & runtime exception

* **Errors** are exceptional scenarios which are out of the scope of applications and it’s not possible to anticipate and recover from them, for example, hardware failure, JVM crash or out of memory error

* **Checked exceptions** are exceptional scenarios that we can anticipate in a program and try to recover from it, for example, FileNotFoundException. We should catch this exception and provide a useful message to the user and log it properly for debugging purpose. ` try...catch... `

* **Runtime exceptions** are caused by bad programming, for example, trying to retrieve an element from the Array. At first, we should check the length of the array before trying to retrieve the element otherwise it might throw ArrayIndexOutOfBoundException at runtime.

## :fire:Generics
```JAVA
public class Box<T> {
    // T stands for "Type"
    private T t;
    public void set(T t) { this.t = t; }
    public T get() { return t; }
}
```
## :fire:JRE or JDK
* JRE: Java Runtime Environment
    * Provides the required environment for Java to run. It mainly includes the standard implementation of the JVM and some basic Java class libraries
* JDK: Java Development Kit
    * Provides the Java development and the running environment
    * The JDK is the core of Java development, integrating the JRE with other tools such as javac, the compiler for compiling Java source code
* JDK>JRE>JVM, The JRE enables Java programs to run, The JDK also supports the development of Java programs
