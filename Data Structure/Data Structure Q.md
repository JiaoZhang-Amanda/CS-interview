## Data Structure Interview Question

### Commonly used Data Structures
- **Arrays**
   - One-dimensional arrays (as shown above)
   - Multi-dimensional arrays (arrays within arrays)
- **Stacks**
- **Queues**
- **Linked List**
   - Singly Linked List (Unidirectional)
   - Doubly Linked List (Bi-directional)
- **Trees**
   - N-ary Tree
   - Balanced Tree
   - Binary Tree
   - Binary Search Tree
   - AVL Tree
   - Red Black Tree
   - 2–3 Tree
- **Graphs**
   - Undirected Graph
   - Directed Graph
- **Tries** (They are effectively trees but it's still good to call them out separately).
- **Hash Tables**

### Common Data Structure Operations
- w*: Worst Time Complexity
- a*: Average Time Complexity

DataStructure|Access(a*)|Search(a*)|Insertion(a*)|Deletion(a*)|Access(w*)|Search(w*)|Insertion(w*)|Deletion(w*)
--|--|--|--|--|--|--|--|--
Array|**O(1)**|O(n)|O(n)|O(n)|**O(1)**|O(n)|O(n)|O(n)
Stack|O(n)|O(n)|**O(1**)|**O(1)**|O(n)|O(n)|**O(1)**|**O(1)**
Queue|O(n)|O(n)|**O(1**)|**O(1)**|O(n)|O(n)|**O(1)**|**O(1)**
LinkedList|O(n)|O(n)|**O(1**)|**O(1)**|O(n)|O(n)|**O(1)**|**O(1)**
Hash Table|N/A|**O(1)**|**O(1)**|**O(1)**|N/A|O(n)|O(n)|O(n)
BST|**O(logn)**|**O(logn)**|**O(logn)**|**O(logn)**|O(n)|O(n)|O(n)|O(n)

### Linear VS Non-linear
- Linear: Array, Stack, Queue, LinkedList
- Non-linear: Graphs, Trees

### Deinifation
- **LinkedList**: A linked list is a sequence of nodes in which each node is connected to the node following it. This forms a chain-like link for data storage.
- **Queue**: A queue is a data structure that can simulate a list or stream of data. In this structure, new elements are inserted at one end, and existing elements are removed from the other end.
- **Stack**: A stack is a data structure in which only the top element can be accessed. As data is stored in the stack, each data is pushed downward, leaving the most recently added data on top.
- **Graph**: A graph is one type of data structure that contains a set of ordered pairs. These ordered pairs are also referred to as edges or arcs and are used to connect nodes where data can be stored and retrieved.
- **Doubld LinkedList**: Doubly linked lists are a special type of linked list wherein traversal across the data elements can be done in both directions. This is made possible by having two links in every node, one that links to the next node and another one that connects to the previous node.
- **Binary Tree**: A binary tree is one type of data structure that has two nodes, a left node, and a right node. In programming, binary trees are an extension of the linked list structures.
- **Binary Search Tree**: A binary search tree stores data in such a way that they can be retrieved very efficiently. The left subtree contains nodes whose keys are less than the node’s key value, while the right subtree contains nodes whose keys are greater than or equal to the node’s key value. Moreover, both subtrees are also binary search trees.
