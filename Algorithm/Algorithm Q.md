## Algorithm Interview Question

### Commonly Algorithm
* Tree Traversal Algorithms: Pre-Order, In-Order, and Post-Order traversal.
* Graph Search Algorithms: Depth First Search (DFS), Breadth First Search (BFS), and Dijkstra’s algorithm, A* 
* Search Algorithms: binary search
* Sorting Algorithms: Bubble sort, insertion sort, selection sort, etc, merge sort and quick sort.

### Sorting Algorithm

Algorithm    | Best-case       |  Worst-case        | Average-case      |   Space Complexity     |    Stable?
--|--|--|--|--|--
Quicksort      | O(nlogn)       |  O(n^2)    |    O(nlogn)     | logn best, n avg     |    Usually not*
Merge Sort      | O(nlogn)       |  O(nlogn)     |    O(nlogn)     |    O(n)       |  Yes
Insertion Sort       |  O(n)     |  O(n^2)     |  O(n^2)     |   O(1)     |  Yes
Bubble Sort      |   O(n)      |   O(n^2)    |  O(n^2)     |  O(1)        | Yes
Heapsort    | O(nlogn)        | O(nlogn)      | O(nlogn)      |   O(1)     |    No
Counting Sort      | O(k+n)       | O(k+n)        | O(k+n)      |   O(k+n)      |   Yes

#### Quicksort 
* A fast sorting algorithm that takes a divide-and-conquer approach to sorting lists.
* Quicksort has a very slow worst-case running time, but a fast average and best-case running time.
* Here is a recursive algorithm for quicksort:
    1) If the list is empty, return the list and terminate. (Base case)
    2) Choose a pivot element in the list.
    3) Take all of the elements that are less than or equal to the pivot and use quicksort on them.
    4) Take all of the elements that are greater than the pivot and use quicksort on them.
    5) Return the concatenation of the quicksorted list of elements that are less than or equal to the pivot, the pivot, and the quicksorted list of elements that are greater than the pivot.
    
#### Merge Sort
* An efficient sorting algorithm that uses a divide-and-conquer approach to order elements in an array.
* Mergesort runs in a guaranteed O(nlogn) time, which is significantly faster than the average- and worst-case running times of several other sorting algorithms.
* Here is the recursive mergesort algorithm:
    1) If the list has only one element, return the list and terminate. (Base case)
    2) Split the list into two halves that are as equal in length as possible. (Divide)
    3) Using recursion, sort both lists using mergesort. (Conquer)
    4) Merge the two sorted lists and return the result. (Combine)
* Pros
    1) Time-efficient with time complexity of O(n \log n)O(nlogn)
    2) Can be used for external sorting
    3) Highly parallelizable
    4) Stable sort
* Cons
    1) Marginally slower than quicksort in practice
    2) Not as space-efficient as other sorting algorithms, e.g. block sort
