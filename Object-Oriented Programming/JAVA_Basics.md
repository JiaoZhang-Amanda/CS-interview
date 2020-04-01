* [Data Type](#data-type)
    * [Primitive Type](#Primitive-type)
    * [Wrapper Classes](#Wrapper-Classes)
    * [Buffer Pool](#Buffer-Pool)
* [String](#String)
    * [String VS StringBuffer VS StringBuiler](#String-VS-StringBuffer-VS-StringBuiler)
    * ["==" VS "equals()"](#==-VS-equals())
    
## Data Type
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
String (or any object)   |    null|-
boolean |    false|-
* The JVM converts Boolean to int at compile time
* Primitive types can never be null.

### Wrapper Classes
A wrapper class is an object that encapsulates a primitive type.
* **Autoboxing**: automatic conversion of primitive types to their corresponding object wrapper classes. e.g. int -> Integer
* **Unboxing**: automatic conversion of object wrapper types into their corresponding primitive types. e.g. Integer -> int
![](https://media.geeksforgeeks.org/wp-content/uploads/Wrapper.png)
* Each wrapper class has Ocbject as a superclass. Byte, Short, Integer, Long Float and Double have Number as their direct superclass. This means that each wrapper class can implement the methods of the Object class such as hashCode(), equals(Object obj), clone(), and toString().
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

## String

