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
- HashTable is synchronized, whereas HashMap is not. Thus, HashMap is better for non-threaded applications.(HashMap can be synchronized by Map m = Collections.synchronizeMap(hashMap))
- HashTable does not allow null keys or values, HashMap allows one null key and any number of null values.

### 5. Explain Mutex
### 6. Explain Semaphore
### 7. What happened when compiling and running JAVA code?
### 8. Generic type
### 9. Stack memory VS Heap memory
