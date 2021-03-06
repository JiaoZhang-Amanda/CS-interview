## Algorithm Interview Question

## Commonly Algorithm

1. Sorting Algorithm: Bubble sort, insertion sort, selection sort, etc, merge sort and quick sort.
2. Graph Search Algorithm: Depth First Search (DFS), Breadth First Search (BFS), and Dijkstra’s algorithm, A* 
3. Tree / Binary Search Tree
4. Dynamic Programming
5. Search / Binary Search
6. String / Array
7. Math / Bit
8. Linked List
9. Design

## Sorting Algorithm

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
```
public class QuickSort {
    public static void sort(int[] nums) {
        quickSort(nums, 0, nums.length - 1);
    }
 
    public static void quickSort(int[] nums, int start, int end) {
        if (start >= end) {
            return;
        }
        int pivot_index = partition(nums, start, end);
        quickSort(nums, start, pivot_index - 1);
        quickSort(nums, pivot_index + 1, end);
    }
 
    public static int partition(int[] nums, int start, int end) {
        int mid = start + (end - start) / 2;
        int pivot = nums[mid];
        while (start < end) {
            while (nums[start] < pivot) {start++;}       
            while (nums[end] > pivot) {end--;}
            // swap
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
        }
        return start;
    }
}
```
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

#### Bucket Sort
```
public static void bucketSort(int[] input) { 
    // get hash codes final int[] code = hash(input); 
    // create and initialize buckets to ArrayList: O(n) 
    List[] buckets = new List[code[1]]; 
    for (int i = 0; i < code[1]; i++) { 
        buckets[i] = new ArrayList(); 
    } 
    // distribute data into buckets: O(n) 
    for (int i : input) { 
        buckets[hash(i, code)].add(i); 
    } 
    // sort each bucket O(n) 
    for (List bucket : buckets) { 
        Collections.sort(bucket); 
    } 
    int ndx = 0; 
    // merge the buckets: O(n) 
    for (int b = 0; b < buckets.length; b++) { 
        for (int v : buckets[b]) { 
            input[ndx++] = v; 
        }
    } 
} 
/** * * @param input * 
@return an array containing hash of input */ 
private static int[] hash(int[] input) { 
    int m = input[0]; 
    for (int i = 1; i < input.length; i++) { 
        if (m < input[i]) { m = input[i]; 
        } 
    } 
    return new int[] { m, (int) Math.sqrt(input.length) }; 
}
```
## Graph Search Algorithm
### Breadth First Search(BFS)
An algorithm for traversing or searching tree or graph data structures. It starts at the tree root (or some arbitrary node of a graph, sometimes referred to as a 'search key'), and explores all of the neighbor nodes at the present depth prior to moving on to the nodes at the next depth level.
* Input: A graph Graph and a starting vertex root of Graph
* Output: Goal state. The parent links trace the shortest path back to root
* Pseudocode
```
procedure BFS(G, start_v) is
      let Q be a queue
      label start_v as discovered
      Q.enqueue(start_v)
      while Q is not empty do
          v := Q.dequeue()
          if v is the goal then
              return v
          for all edges from v to w in G.adjacentEdges(v) do
             if w is not labeled as discovered then
                 label w as discovered
                 w.parent := v
                 Q.enqueue(w)
```
* Time O(n+m)
* Space O(n) 

### Depth-first search(DFS)
An algorithm for traversing or searching tree or graph data structures. The algorithm starts at the root node (selecting some arbitrary node as the root node in the case of a graph) and explores as far as possible along each branch before backtracking.
* Input: A graph G and a vertex v of G
* Output: All vertices reachable from v labeled as discovered
* Recursive
```
procedure DFS(G, v) is
label v as discovered
for all directed edges from v to w that are in G.adjacentEdges(v) do
    if vertex w is not labeled as discovered then
        recursively call DFS(G, w)
```
* Iterative
```
procedure DFS-iterative(G, v) is
let S be a stack
S.push(v)
while S is not empty do
    v = S.pop()
    if v is not labeled as discovered then
        label v as discovered
        for all edges from v to w in G.adjacentEdges(v) do 
            S.push(w)
```
* Time O(n+m)
* Space O(n) 

### Topological sort
Topological sorting for **Directed Acyclic Graph (DAG)** is a linear ordering of vertices such that for every directed edge uv, vertex u comes before v in the ordering.
* Time O(n+m)
* Using DFS or BFS

### Union Find(Disjoint Set Union)
A union-find algorithm is an algorithm that performs two useful operations on such a data structure:

* Find: Determine which subset a particular element is in. This can be used for determining if two elements are in the same subset.
* Union: Join two subsets into a single subset.

Union-Find Algorithm can be used to check whether an **undirected graph** contains cycle or not. 
```
public int find(int p){
    while(p != id[p]) p = id[p];
    return p;
}

public void union(int p, int q){
    int pRoot = find(p);
    int qRoot = find(q);
    if(pRoot == qRoot) return;
    id[p] = qRoot;
    count--;
}
```
* Time O(m+n)
* Space O(n) 

### Dijkstra’s algorithm
An algorithm for finding the shortest paths between nodes in a graph, which may represent
* Solves the single-source shortest path problem with non-negative edge weight.
* Using a priority queue
```
  function Dijkstra(Graph, source):
      dist[source] ← 0                           // Initialization

      create vertex priority queue Q

      for each vertex v in Graph:           
          if v ≠ source
              dist[v] ← INFINITY                 // Unknown distance from source to v
              prev[v] ← UNDEFINED                // Predecessor of v

         Q.add_with_priority(v, dist[v])


     while Q is not empty:                      // The main loop
         u ← Q.extract_min()                    // Remove and return best vertex
         for each neighbor v of u:              // only v that are still in Q
             alt ← dist[u] + length(u, v) 
             if alt < dist[v]
                 dist[v] ← alt
                 prev[v] ← u
                 Q.decrease_priority(v, alt)

     return dist, prev
```
### A*
A graph traversal and path search algorithm, which is often used in computer science due to its completeness, optimality, and optimal efficiency. One major p.ractical drawback is its O(b^d) space complexity, as it stores all generated nodes in memory. 


## Tree / Binary Search Tree
* Tree construction, traversal and manipulation algorithms
* one flavor of balanced binary tree, whether it's a red/black tree, a splay tree or an AVL tree and how it's implemented. 
* there are three basic ways to represent a graph in memory (objects and pointers, matrix and adjacency list), and you should familiarize yourself with each representation and its pros and cons. 
* difference between inorder, postorder and preorder traversal (for trees). their computational complexity, tradeoffs and how to implement them in real code. 

### Binary trees, N-ary trees and Trie-trees
* A **binary tree** is a rooted tree in which each node has no more than 2 children.
*  If a tree is a rooted tree in which each node has no more than N children, it is called **N-ary tree**
* **Trie** is one of the most frequently used N-ary trees
```
class Trie {
    TrieNode root;
    public Trie(String[] strs) {
        root = new TrieNode();
        for (String str: strs) {
            TrieNode cur = root;
            for (char ch: str.toCharArray()) {
                int index = ch-'a';
                if (cur.children[index] == null) cur.children[index] = new TrieNode();
                cur.children[index].words.add(str);
                cur = cur.children[index];
            }
        }
    }
    
    public List<String> getWords(String prefix) {
        List<String> res = new ArrayList<>();
        TrieNode cur = root;
        for (char ch: prefix.toCharArray()) {
            int index = ch-'a';
            if (cur.children[index] == null) return res;
            cur = cur.children[index];
        }
        res.addAll(cur.words);
        return res;
    }
}

class TrieNode {
    TrieNode[] children;
    List<String> words;
    public TrieNode() {
        children = new TrieNode[26];
        words = new ArrayList<>();
    }
}
```
### Tree Traversal
* preorder: visit the root node, then traverse the left subtree and finally traverse the right subtree.
* inorder: traverse the left subtree, then visit the root node and finally traverse the right subtree.
* postorder: traverse the left subtree, then traverse the right subtree and finally visit the root node.
* level-order: traverse the tree level by level.

## Dynamic Programming


## Searching Algorithm
### Linear Search / sequential search
### Binary Search
Binary Search is generally composed of 3 main sections:
* Pre-processing — Sort if collection is unsorted.
* Binary Search — Using a loop or recursion to divide search space in half after each comparison.
* Post-processing — Determine viable candidates in the remaining space.
