* [Data Type](#firedata-type)
    * [Primitive Type](#Primitive-type)
    * [Wrapper Classes](#Wrapper-Classes)
    * [Buffer Pool](#Buffer-Pool)
* [String](#fireString)
    * [Principle -- Why Immutable?](#principle----why-immutable)
    * [Immutable Benefits](#Immutable-Benefits)
    * [String VS StringBuffer VS StringBuiler](#string-stringbuffer-and-stringbuilder)
    
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
```
Integer x = new Integer(123);
Integer y = new Integer(123);
System.out.println(x == y);    // false
Integer z = Integer.valueOf(123);
Integer k = Integer.valueOf(123);
System.out.println(z == k);   // true
```
* When arguments on both sides of the “==” operator are objects, no unboxing will occur and the “==” operator will compare the **object’s reference** in memory.
* "==" between The wrapper type and the primitive type: automatically converts the wrapper type to the primitive type, and then compares the values `new Integer（123）==123 //true`
```
Integer m = 123;
Integer n = 123;
System.out.println(m == n); // true
```
* The compiler calls the valueOf() method during autoboxing, so multiple instances of an Integer with the same value and the value within the cache pool are created using autoboxing, and the same object is referenced.

## :fire:String
### Principle -- Why Immutable?
* String is declared final, so it cannot be inherited. (wrapper classes such as Integer cannot be inherited)
* Java8
```
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {
    /** The value is used for character storage. */
    private final char value[];
}
```
* Java9
```
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {
    /** The value is used for character storage. */
    private final byte[] value;

    /** The identifier of the encoding used to encode the bytes in {@code value}. */
    private final byte coder;
}
```
* The value array is declared final, which means that after the value array has been initialized, it cannot refer to any other array. And there is no way to change the value array inside String, so you can guarantee that String is **immutable**.
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
