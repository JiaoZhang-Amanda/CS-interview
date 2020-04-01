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
```
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
```
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
```
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
```
int myInt = 9;
double myDouble = myInt; // Automatic casting: int to double
double myDouble = 9.78;
int myInt = (int) myDouble; // Manual casting: double to int
```
* **Implicit Type Conversion**
    * Java's +=, -=, *=, /= compound assignment operators doesn't require casting
    * Using the += or ++ operator performs implicit type conversions.
```
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
```
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
```
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
```
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
```
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
```
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
