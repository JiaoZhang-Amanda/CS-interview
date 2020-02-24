## C/C++ Interview Question

### Explain what is the use of void main () in C++ language?
To run the C++ application it involves two steps, the first step is a compilation where conversion of C++ code to object code take place. While second step includes linking, where combining of object code from the programmer and from libraries takes place. This function is operated by main () in C++ language.

### Explain what is C++ objects?
Class gives blueprints for object, so basically an object is created from a class or in other words an object is an instance of a class. The data and functions are bundled together as a self-contained unit called an object. Here, in the example A and B is the Object.

### Define basic type of variable used for a different condition in C++?
The variable used for a different condition in C++ are
• Bool: Variable to store boolean values (true or false)
• Char: Variable to store character types
• int : Variable with integral values
• float and double: Types of variables with large and floating point values

### What is namespace std; and what is consists of?
Namespace std; defines your standard C++ library, it consists of classes, objects and functions of the standard C++ library. You can specify the library by using namespace std or std: : throughout the code. Namespace is used to differentiate the same functions in a library by defining the name.

### Explain what is Loop function? What are different types of Loops?
In any programming language, to execute a set of statements repeatedly until a particular condition is satisfied Loop function is used. The loop statement is kept under the curly braces { } referred as Loop body.
In C++ language, three types of loops are used
• While loop
• For loop
• Do-while loop

### When should we use pointers in a C program?
* To get address of a variable
* For achieving pass by reference in C: Pointers allow different functions to share and modify their local variables.
* To pass large structures so that complete copy of the structure can be avoided.
* To implement “linked” data structures like linked lists and binary trees.

### What is NULL pointer?
NULL is used to indicate that the pointer doesn’t point to a valid location. Ideally, we should initialize pointers as NULL if we don’t know their value at the time of declaration. Also, we should make a pointer NULL when memory pointed by it is deallocated in the middle of a program.

### What is the difference between call by value and call by reference in C？

。|Call by value|Call by reference
--|--|--
Description|When a copy of the value is passed to the function, then the original value is not modified.|When a copy of the value is passed to the function, then the original value is modified.
Memory location  |  Actual arguments and formal arguments are created in separate memory locations.   | Actual arguments and formal arguments are created in the same memory location.
Safety   | In this case, actual arguments remain safe as they cannot be modified.   | In this case, actual arguments are not reliable, as they are modified.
Arguments  |  The copies of the actual arguments are passed to the formal arguments.  |  The addresses of actual arguments are passed to their respective formal arguments.

### Memory errors
[link](https://www.cprogramming.com/tutorial/memory_debugging_parallel_inspector.html)
* Applications that have memory errors can experience major problems. For example, memory leaks can cause an application to run out of memory resulting in the termination of the application, gracefully or otherwise.
* Memory errors can be broadly classified into Heap Memory Errors and Stack Memory Errors. 
1. Invalid Memory Access in heap and stack
This error occurs when a read or write instruction references unallocated or deallocated memory.

```(C++)
char *pStr = (char*) malloc(25); 
free(pStr); 
strcpy(pStr, .parallel programming.); // Invalid write to deallocated memory in heap
```

2. Memory leak
Memory leaks occur when memory is allocated but not released. If such leaks happen often enough and frequently enough, the leaks will eventually cause the application to run out of memory resulting in a premature termination (gracefully or as a crash).
3. Mismatched Allocation/Deallocation
This error occurs when a deallocation is attempted with a function that is not the logical counterpart of the allocation function used.
4. Missing Allocation
This error occurs when freeing memory which has already been freed. This is also called "repeated free" or "double free".
5. Uninitialized Memory Access in heap and stack
This type of memory error will occur when an uninitialized variable is read in your application.
6. Cross Stack Access
This occurs when a thread accesses stack memory of a different thread.

### Smart Pointers
```
MyClass *ptr = new MyClass(); 
ptr->doSomething(); 
//  We must do delete(ptr) to avoid memory leak
```
Using smart pointers, we can make pointers to work in way that we don’t need to explicitly call delete. Smart pointer is a wrapper class over a pointer with operator like * and -> overloaded. The objects of smart pointer class look like pointer, but can do many things that a normal pointer can’t like automatic destruction (yes, we don’t have to explicitly use delete), reference counting and more.

### Virtual destructor
Destructors in the Base class can be Virtual. Whenever Upcasting is done, Destructors of the Base class must be made virtual for proper destrucstion of the object when the program exits.
* NOTE: Constructors are never Virtual, only Destructors can be Virtual.
* A normal destructor is set to be just that a normal destructor that the class has implementation for and nowhere else. A virtual destructor can be customized for the task at hand because it can be overriden. So if anywhere you need to change the behavior of the destructor you should make it virtual.

### Static Keyword
Static keyword has different meanings when used with different types. We can use static keyword with:
* Static Variables : Variables in a function, Variables in a class
    * Static variables in a Function: When a variable is declared as static, space for it gets allocated for the lifetime of the program.
    * Static variables in a class: As the variables declared as static are initialized only once as they are allocated space in separate static storage so, the static variables in a class are shared by the objects.
* Static Members of Class : Class objects and Functions in a class
    * Class objects as static: Just like variables, objects also when declared as static have a scope till the lifetime of program.
    * Static member functions: are allowed to access only the static data members or other static member functions, they can not access the non-static data members or member functions of the class.
    
### What is the difference between vector and list?
* Both vector and list are sequential containers of C++ Standard Template Library. 
* List stores elements at non contiguous memory location i.e. it internally uses a doubly linked list, Whereas, vector stores elements at contiguous memory locations like an array.
* Types of STL
    * vector: dynamic array -- efficient at random access, and add/delete at end.
    * list : doubly-linked list -- efficient at forward/backward traversal, and insertion anywhere.
    * forward_list : singly-linked list -- efficient at forward traversal, and insertion anywhere.
    * deque : doubled ended queue -- dynamic array that also allows for efficient add/delete at beginning
    * array : static array -- size fixed at compile time.
       
#### how multiple inheritance works
* Multiple Inheritance is a feature of C++ where a class can inherit from more than one classes.
* The constructors of inherited classes are called in the same order in which they are inherited.
* The destructors are called in reverse order of constructors.



