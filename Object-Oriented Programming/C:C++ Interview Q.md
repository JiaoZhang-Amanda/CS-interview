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

 |Call by value|Call by reference
--|--|--
Description|When a copy of the value is passed to the function, then the original value is not modified.|When a copy of the value is passed to the function, then the original value is modified.
Memory location  |  Actual arguments and formal arguments are created in separate memory locations.   | Actual arguments and formal arguments are created in the same memory location.
Safety   | In this case, actual arguments remain safe as they cannot be modified.   | In this case, actual arguments are not reliable, as they are modified.
Arguments  |  The copies of the actual arguments are passed to the formal arguments.  |  The addresses of actual arguments are passed to their respective formal arguments.
