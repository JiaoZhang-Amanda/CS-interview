* [Container Type](#fireContainer-Type)
    * [Collection](#Collection)
    * [Map](#Map)

## :fire:Container Type
* The Collection interface and Map interface are the two main “root” interfaces of Java collection classes.
### Collection 
`java.util.Collection`
![](https://camo.githubusercontent.com/d1efb1abc3173aa2a607316dda79bea560fe333f/68747470733a2f2f63732d6e6f7465732d313235363130393739362e636f732e61702d6775616e677a686f752e6d7971636c6f75642e636f6d2f696d6167652d32303139313230383232303934383038342e706e67)
* **Set** : Doesn't allow duplicates and unordered collection. Set just allow one null element as there is no duplicate permitted
    * **HashSet**: Hashing based. Search O(1)
    * **TreeSet**: balanced BST based. Note that TreeSet implements SortedSet. Search O(logn)
    * **LinkedHashSet**
* **List** : Can contain duplicates and elements are ordered. List's contract maintains insertion order or element. The list allows null elements and you can have many null objects in a List because it also allowed duplicates.
    * **ArrayList**: dynamic array based. non-synchronized, multiple threads can work on ArrayList at the same time.
    * **LinkedList**: linked list based. A linked list is a sequence of nodes in which each node is connected to the node following it. This forms a chain-like link for data storage. LinkedList can be used as a stack, queue, and dequeue. LinkedList is faster in add and remove, but slower in get.
    * **Vector**: similar with ArrayList but it is synchronized and thread-safe. ArrayList grow by half of its size when resized while Vector doubles the size of itself by default when grows.
* **Queue** : Typically order elements in FIFO order
    * **PriorityQueue**: Based on the heap structure.
* **Deque** : Elements can be inserted and removed at both ends. Allows both LIFO and FIFO. 

### Map
`java.util.Map`
![](https://camo.githubusercontent.com/cd126ae7572489beead8b33f3a26a5a0bb1f288e/68747470733a2f2f63732d6e6f7465732d313235363130393739362e636f732e61702d6775616e677a686f752e6d7971636c6f75642e636f6d2f696d6167652d32303139313230383232343735373835352e706e67)
* Map holds two objects per Entry. e.g. a key and a value and It may contain duplicate values but keys are always unique.
* Contains Key value pairs. Doesn't allow duplicates. Can have null values and at most one null key. 
* **HashTable**: synchronized and thread-safe(can be shared with many threads). HashTable does not allow null keys or values
* **HashMap**: Hashing based. HashMap data structure contains Key-Value pairs. All the keys in a HashMap data structure are unique. The values are not necessarily be unique. Different keys may correspond to same value. non-synchronized and not thread-safe. better for non-threaded applications. HashMap allows one null key and any number of null values.
* **TreeMap**: TreeMap implements SortedMap.  
* **LinkedHashMap**
