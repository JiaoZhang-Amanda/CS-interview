# C/C++ Interview Question
### What is the difference between C and C++?
The major difference between C and C++ is that C is a procedural programming language and does not support classes and objects, while C++ is a combination of both procedural and object oriented programming language; therefore C++ can be called a hybrid language.

C|C++
--|--
When compared to C++, C is a subset of C++.|C++ is a superset of C. C++ can run most of C code while C cannot run C++ code.
C supports procedural programming paradigm for code development.|C++ supports both procedural and object oriented programming paradigms; therefore C++ is also called a hybrid language.
C does not support object oriented programming; therefore it has no support for polymorphism, encapsulation, and inheritance.|Being an object oriented programming language C++ supports polymorphism, encapsulation, and inheritance.
data and functions are separate and free entities.|data and functions are encapsulated together in form of an object. For creating objects class provides a blueprint of structure of the object.
C does not have namespace feature.|C++ uses NAMESPACE which avoid name collisions.
C uses functions for input/output. For example scanf and printf.|C++ uses objects for input output. For example cin and cout.
 C provides malloc() and calloc() functions for dynamic memory allocation, and free() for memory de-allocation.|C++ provides new operator for memory allocation and delete operator for memory de-allocation.
 C does not provide direct support for error handling (also called exception handling)|C++ provides support for exception handling. Exceptions are used for "hard" errors that make the code incorrect.
 
 ## [C]
 ### Memory Layout of C Programs
 ![](https://media.geeksforgeeks.org/wp-content/uploads/memoryLayoutC.jpg)
 1. **Text segment**
     * also known as a code segment or simply as text, is one of the sections of a program in an object file or in memory, which contains **executable instructions**.
     * the text segment is sharable so that only a single copy needs to be in memory for frequently executed programs, such as text editors, the C compiler, the shells, and so on. Also, the text segment is often read-only, to prevent a program from accidentally modifying its instructions.
 2. **Initialized data segment** Data
     * Initialized data segment, usually called simply the **Data Segment**. A data segment is a portion of virtual address space of a program, which contains the **global variables** and **static variables** that are initialized by the programmer.
     * Note that, data segment is not read-only, since the values of the variables can be altered at run time.
     * This segment can be further classified into initialized read-only area and initialized read-write area.
 3. **Uninitialized data segment** BSS
    * Uninitialized data segment, often called the **BSS segment**, named after an ancient assembler operator that stood for “block started by symbol.” Data in this segment is initialized by the kernel to arithmetic 0 before the program starts executing
    * uninitialized data starts at the end of the data segment and contains all **global variables** and **static variables** that are initialized to zero or do not have explicit initialization in source code.
 4. **Stack**
     * The stack area traditionally adjoined the heap area and grew the opposite direction; when the stack pointer met the heap pointer, free memory was exhausted. 
     * The stack area contains the program stack, a LIFO structure, typically located in the higher parts of memory.
     * The stack grows down into unused space while the heap grows up.
     * Functions and variable are declared on the stack. 
 5. **Heap**
     * Heap is the segment where *dynamic memory* allocation usually takes place.
     * The heap area begins at the end of the BSS segment and grows to larger addresses from there.
     * The Heap area is managed by malloc, realloc, and free, which may use the brk and sbrk system calls to adjust its size
     
### Storage classes in C.
A storage class represents the visibility and a location of a variable. It tells from what part of code we can access a variable. a storage class is used to represent the information about a variable. A storage class is used to describe the following things:
* The variable scope.
* The location where the variable will be stored.
* The initialized value of a variable.
* A lifetime of a variable.
* Who can access a variable?
Four types: 

Storage class | Purpose
--|--
auto | It is a default storage class.
extern | It is a global variable.
static | It is a local variable which is capable of returning a value even when control is transferred to the function call.
register |  It is a variable which is stored inside a Register.

### What is the difference between Macro and typedef?
* Typedef defines a new data type. Macros can be of any type. Macros can even be any code block containing statements, loops, function calls etc.
`typedef <existing_name> <alias_name>`
`#define MAX 1000`
* typedef interpretation is performed by the compiler where #define statements are performed by preprocessor. Macros are expanded by the preprocessor before compilation takes place.
* #define should not be terminated with a semicolon, but typedef should be terminated with semicolon.
* #define will just copy-paste the definition values at the point of use, while typedef is the actual definition of a new type.

### Why is Macro useful in C
* The inline keyword was not standard in the C language. Thus macros allowed you to inline small functions. They also in some ways work like templates
* Macro execution is faster than function execution because in function, much of time is used to take control from function call to called function and much of time is spent in this process. Whereas in macro expression are directly replaced in the source code.Much of time is spent in the binding of the function to the caller function.It is first time when i m reply any question .

### C Data Types
There are 4 types of data –
* Basic Data Types: **int**, **float**, **char**, **double**
```
char name[25];
int id;
float marks[5];
double interest;
```
* Derived: **Array**, **pointers**, **struct** and **union**
* Void: an empty data type used as a return type for functions.
* Enumeration: If you have integer constants in the code that can be reused or clubbed together, we can use enums to define the constants. The most common example of this is days of the week.
```
enum weekdays;
enum weekend;
```
### When should we use pointers in a C program?
* To get address of a variable
* For achieving pass by reference in C: Pointers allow different functions to share and modify their local variables.
* To pass large structures so that complete copy of the structure can be avoided.
* To implement “linked” data structures like linked lists and binary trees.

### What is NULL pointer?
NULL is used to indicate that the pointer doesn’t point to a valid location. Ideally, we should initialize pointers as NULL if we don’t know their value at the time of declaration. Also, we should make a pointer NULL when memory pointed by it is deallocated in the middle of a program.

### Structures VS Union
* Structure is a user-defined datatype in C language which allows us to combine data of different types together. Structure helps to construct a complex data type which is more meaningful. It is somewhat similar to an Array, but an array holds data of similar type only. But structure on the other hand, can store data of any type, which is practical more useful.
```
struct [structure_tag]
{
    //member variable 1
    //member variable 2
    //member variable 3
    ...
}[structure_variables];
```
* A union is a special data type available in C that allows storing different data types in the same memory location. You can define a union with many members, but only one member can contain a value at any given time. Unions provide an efficient way of using the same memory location for multiple purposes.
```
union [union name]
{
   member definition;
   member definition;
   ...
   member definition;
};
```
* Similarities between Structure and Union
    * Both are user-defined data types used to store data of different types as a single unit.
    * Their members can be objects of any type, including other structures and unions or arrays. A member can also consist of a bit field.
    * Both structures and unions support only assignment = and sizeof operators. The two structures or unions in the assignment must have the same members and member types.
    * A structure or a union can be passed by value to functions and returned by value by functions. The argument must have the same type as the function parameter. A structure or union is passed by value just like a scalar variable as a corresponding parameter.
    * ‘.’ operator is used for accessing members.
* Differences
![](https://media.geeksforgeeks.org/wp-content/uploads/Structure-vs-Union.png)

### Bit Fields in C
In C, we can specify size (in bits) of structure and union members. The idea is to use memory efficiently when we know that the value of a field or group of fields will never exceed a limit or is withing a small range.
```
// Space optimized representation of the date 
struct date { 
    // d has value between 1 and 31, so 5 bits 
    // are sufficient 
    unsigned int d : 5; 
  
    // m has value between 1 and 12, so 4 bits 
    // are sufficient 
    unsigned int m : 4; 
  
    unsigned int y; 
}; 
```

### What is the difference between call by value and call by reference in C？

。|Call by value|Call by reference
--|--|--
Description|When a copy of the value is passed to the function, then the original value is not modified.|When a copy of the value is passed to the function, then the original value is modified.
Memory location  |  Actual arguments and formal arguments are created in separate memory locations.   | Actual arguments and formal arguments are created in the same memory location.
Safety   | In this case, actual arguments remain safe as they cannot be modified.   | In this case, actual arguments are not reliable, as they are modified.
Arguments  |  The copies of the actual arguments are passed to the formal arguments.  |  The addresses of actual arguments are passed to their respective formal arguments.

### volatile keyword
* The volatile keyword is intended to prevent the compiler from applying any optimizations on objects that can change in ways that cannot be determined by the compiler. 
* Objects declared as volatile are omitted from optimization because their values can be changed by code outside the scope of current code at any time.
* `volatile int foo;`/ `int volatile foo;`

### Compiling a C program: Behind the Scenes
* C is a high-level language and it needs a compiler to convert it into an executable code so that the program can be run on our machine.
* Compiler converts a C program into an executable. There are four phases for a C program to become an executable:
1) **Pre-processing**: The preprocessed output is stored in the *filename.i*.
    * Removal of Comments
    * Expansion of Macros
    * Expansion of the included files.
    * Conditional compilation
    ==> what does ## is in the preprocessor?
    `##` , token concatenation, tells the preprocessor to concatenate the left and right sides, and concatenates two tokens into one token.
```
#define DECLARE_STRUCT_TYPE(name) typedef struct name##_s name##_t    DECLARE_STRUCT_TYPE(g_object); // Outputs: typedef struct g_object_s g_object_t;
```
2) **Compilation**: compile filename.i and produce an intermediate compiled output file `filename.s`. it is in **assembly language**, which assembler can understand.
    * An assembly language is a low-level programming language designed for a specific type of processor. It may be produced by compiling source code from a high-level programming language (such as C/C++) but can also be written from scratch. Assembly code can be converted to machine code using an assembler.
3) **Assembly**: the filename.s is taken as input and turned into `filename.o` by assembler. This file contain machine level instructions. At this phase, only existing code is converted into machine language, the function calls like printf() are not resolved.
    * A .o object file file (also .obj on Windows) contains compiled object code (that is, machine code produced by your C or C++ compiler), together with the names of the functions and other objects the file contains. 
    * Object files are processed by the linker to produce the final executable.
4) **Linking**: This is the final phase in which all the linking of function calls with their definitions are done. Linker knows where all these functions are implemented. Linker does some extra work also, it adds some extra code to our program which is required when the program starts and ends. 

### String related function in C
Strings are defined as an array of characters. The difference between a character array and a string is the string is terminated with a special character ‘\0’.
strcat(): append a copy of the source string to the end of destination string. The strcat() function takes two arguments: dest & src, returns dest, the pointer to the destination string.
strrchr(): Returns a pointer to the last occurrence of a character in a string. char *strrchr(const char *str, int c) 
strcmp(): compare these two strings lexicographically. int strcmp(const char *leftStr, const char *rightStr );
strcpy():  copy one string to another. char* strcpy(char* dest, const char* src); returns a pointer to the destination string.
strlen(): calculates the length of a given string.
strncat(): appends not more than n characters from the string pointed to by src to the end of the string pointed to by dest plus a terminating Null-character. strncat(dest, src, 5);

## [C++]
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





## [Memory]
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

### How to find identify memory leaking
* **Valgrind**: Valgrind is a multipurpose code profiling and memory debugging tool for Linux when on the x86 and, as of version 3, AMD64, architectures. It allows you to run your program in Valgrind's own environment that monitors memory usage such as calls to malloc and free (or new and delete in C++). If you use uninitialized memory, write off the end of an array, or forget to free a pointer, Valgrind can detect it.

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
       
### How multiple inheritance works
* Multiple Inheritance is a feature of C++ where a class can inherit from more than one classes.
* The constructors of inherited classes are called in the same order in which they are inherited.
* The destructors are called in reverse order of constructors.

### copy and deep copy
### long long int VS int in java
### map libraray in C++(->second)
