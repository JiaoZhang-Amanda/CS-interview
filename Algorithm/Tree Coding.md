## Tree Coding

### JAVA releted
Trie
```
public TrieNode buildTrie(String[] words) {
    TrieNode root = new TrieNode();
    for (String w : words) {
        TrieNode p = root;
        for (char c : w.toCharArray()) {
            int i = c - 'a';
            if (p.next[i] == null) p.next[i] = new TrieNode();
            p = p.next[i];
        }
        p.word = w;
    }
    return root;
}

class TrieNode {
    TrieNode[] next = new TrieNode[26];
    String word;
}
```

### Leetcode

\#| Title|Difficulty|--
--|--|--|--
257    | Binary Tree Paths  |  Easy|path
298    | Binary Tree Longest Consecutive Sequence   | Medium|path
549   | Binary Tree Longest Consecutive Sequence II    |Medium|path
687	|Longest Univalue Path	|Easy|path
173   | Binary Search Tree Iterator  |  Medium|Traverse 
545  |  Boundary of Binary Tree   | Medium|Traverse
145   | Binary Tree Postorder Traversal   | Hard|Traverse
314| Binary Tree Vertical Order Traversal|Medium|Traverse 
652   | Find Duplicate Subtrees  |  Medium|
501   | Find Mode in Binary Search Tree   | Easy|
889    |Construct Binary Tree from Preorder and Postorder Traversal   | Medium|
270    |Closest Binary Search Tree Value  |  Easy|
272    |Closest Binary Search Tree Value II  |  Hard|
230    | Kth Smallest Element in a BST  |  Medium|
366   | Find Leaves of Binary Tree   | Medium|Search
297  |  Serialize and Deserialize Binary Tree  |  Hard|
449   | Serialize and Deserialize BST  |  Medium|
1376 |   Time Needed to Inform All Employees    |Medium|
96  |  Unique Binary Search Trees  |  Medium|
834  |  Sum of Distances in Tree   | Hard|
337 |   House Robber III |   Medium|
450| Delete Node in a BST|Medium|

<details>
<summary>257. Binary Tree Paths</summary>
 <a href = "https://leetcode.com/problems/binary-tree-paths/">Leetcode Link</a><br>
Given a binary tree, return all root-to-leaf paths.

Note: A leaf is a node with no children.

Example:

Input:

     1
    /  \
    2   3
    \
     5

Output: ["1->2->5", "1->3"]
</details>

<details>
<summary>298. Binary Tree Longest Consecutive Sequence</summary>
<a href = "https://leetcode.com/problems/binary-tree-longest-consecutive-sequence/">Leetcode Link</a><br>
Given a binary tree, find the length of the longest consecutive sequence path.

The path refers to any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The longest consecutive path need to be from parent to child (cannot be the reverse).

For example,

    1
    \
     3
    / \
    2   4
        \
         5
         
<br>Longest consecutive sequence path is 3-4-5, so return 3.
</details>

<details>
<summary>549. Binary Tree Longest Consecutive Sequence II</summary>
<a href = "https://leetcode.com/problems/binary-tree-longest-consecutive-sequence-ii/">Leetcode Link</a><br>
Given a binary tree, you need to find the length of Longest Consecutive Path in Binary Tree.

Especially, this path can be either increasing or decreasing. For example, [1,2,3,4] and [4,3,2,1] are both considered valid, but the path [1,2,4,3] is not valid. On the other hand, the path can be in the child-Parent-child order, where not necessarily be parent-child order.

Example 1:

Input:

        2
       / \
      1   3
Output: 3
Explanation: The longest consecutive path is [1, 2, 3] or [3, 2, 1].
</details>

<details>
<summary>687. Longest Univalue Path</summary>

Given a binary tree, find the length of the longest path where each node in the path has the same value. This path may or may not pass through the root.

The length of path between two nodes is represented by the number of edges between them.


Example 1:

Input:

              5
             / \
            4   5
           / \   \
          1   1   5
Output: 2
</details>

<details>
<summary>173. Binary Search Tree Iterator</summary>
Implement an iterator over a binary search tree (BST). Your iterator will be initialized with the root node of a BST.

Calling next() will return the next smallest number in the BST.
</details>

<details>
<summary>545. Boundary of Binary Tree </summary>
Given a binary tree, return the values of its boundary in anti-clockwise direction starting from root. Boundary includes left boundary, leaves, and right boundary in order without duplicate nodes.

Left boundary is defined as the path from root to the left-most node. Right boundary is defined as the path from root to the right-most node. If the root doesn't have left subtree or right subtree, then the root itself is left boundary or right boundary. Note this definition only applies to the input binary tree, and not applies to any subtrees.

The left-most node is defined as a leaf node you could reach when you always firstly travel to the left subtree if exists. If not, travel to the right subtree. Repeat until you reach a leaf node.

The right-most node is also defined by the same way with left and right exchanged.

Example 1
Input:

    ____1_____
    /          \
    2            3
    / \          / 
    4   5        6   
    / \      / \
    7   8    9  10  
       
Ouput:
[1,2,4,7,8,9,10,6,3]
</details>

<details>
<summary>145. Binary Tree Postorder Traversal</summary>
Given a binary tree, return the postorder traversal of its nodes' values.

Example:

Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [3,2,1]
</details>

<details>
<summary>314. Binary Tree Vertical Order Traversal</summary>
Given a binary tree, return the vertical order traversal of its nodes' values. (ie, from top to bottom, column by column).

If two nodes are in the same row and column, the order should be from left to right.

Examples 1:

Input: [3,9,20,null,null,15,7]

   3
  /\
 /  \
 9  20
    /\
   /  \
  15   7 
</details>

<details>
<summary>652. Find Duplicate Subtrees</summary>
Given a binary tree, return all duplicate subtrees. For each kind of duplicate subtrees, you only need to return the root node of any one of them.

Two trees are duplicate if they have the same structure with same node values.

        1
       / \
      2   3
     /   / \
    4   2   4
       /
      4
The following are two duplicate subtrees:

      2
     /
    4
and

    4
</details>

<details>
<summary>501. Find Mode in Binary Search Tree</summary>
Given a binary search tree (BST) with duplicates, find all the mode(s) (the most frequently occurred element) in the given BST.

Assume a BST is defined as follows:

The left subtree of a node contains only nodes with keys less than or equal to the node's key.
The right subtree of a node contains only nodes with keys greater than or equal to the node's key.
Both the left and right subtrees must also be binary search trees.
 

For example:
Given BST [1,null,2,2],

   1
    \
     2
    /
   2
 

return [2].
</details>

<details>
<summary>889. Construct Binary Tree from Preorder and Postorder Traversal </summary>
Return any binary tree that matches the given preorder and postorder traversals.

Values in the traversals pre and post are distinct positive integers.
Example 1:
Input: pre = [1,2,4,5,3,6,7], post = [4,5,2,6,7,3,1]
Output: [1,2,3,4,5,6,7]
</details>

<details>
<summary>270. Closest Binary Search Tree Value</summary>
Given a non-empty binary search tree and a target value, find the value in the BST that is closest to the target.

Note:

Given target value is a floating point.
You are guaranteed to have only one unique value in the BST that is closest to the target.
</details>

<details>
<summary>272. Closest Binary Search Tree Value II </summary>
Given a non-empty binary search tree and a target value, find k values in the BST that are closest to the target.

Note:

Given target value is a floating point.
You may assume k is always valid, that is: k≤ total nodes.
You are guaranteed to have only one unique set of k values in the BST that are closest to the target.
Example:

Input: root = [4,2,5,1,3], target = 3.714286, and k = 2

    4
   / \
  2   5
 / \
1   3

Output: [4,3]
</details>

<details>
<summary>230. Kth Smallest Element in a BST </summary>
Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.

Note:
You may assume k is always valid, 1 ≤ k ≤ BST's total elements.

Example 1:

Input: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
Output: 1
</details>

<details>
<summary>366. Find Leaves of Binary Tree</summary>
Given a binary tree, collect a tree's nodes as if you were doing this: Collect and remove all leaves, repeat until the tree is empty.

Example:

Input: [1,2,3,4,5]
  
          1
         / \
        2   3
       / \     
      4   5    

Output: [[4,5,3],[2],[1]]
 

Explanation:

1. Removing the leaves [4,5,3] would result in this tree:

          1
         / 
        2  
</details>

<details>
<summary>297. Serialize and Deserialize Binary Tree </summary>
Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

Example: 

You may serialize the following tree:

    1
   / \
  2   3
     / \
    4   5

as "[1,2,3,null,null,4,5]"
</details>

<details>
<summary>449. Serialize and Deserialize BST</summary>
Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary search tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary search tree can be serialized to a string and this string can be deserialized to the original tree structure.

The encoded string should be as compact as possible.

Note: Do not use class member/global/static variables to store states. Your serialize and deserialize algorithms should be stateless.
</details>

<details>
<summary>1376. Time Needed to Inform All Employees</summary>
A company has n employees with a unique ID for each employee from 0 to n - 1. The head of the company has is the one with headID.

Each employee has one direct manager given in the manager array where manager[i] is the direct manager of the i-th employee, manager[headID] = -1. Also it's guaranteed that the subordination relationships have a tree structure.

The head of the company wants to inform all the employees of the company of an urgent piece of news. He will inform his direct subordinates and they will inform their subordinates and so on until all employees know about the urgent news.

The i-th employee needs informTime[i] minutes to inform all of his direct subordinates (i.e After informTime[i] minutes, all his direct subordinates can start spreading the news).

Return the number of minutes needed to inform all the employees about the urgent news.

 

Example 1:

Input: n = 1, headID = 0, manager = [-1], informTime = [0]
Output: 0
Explanation: The head of the company is the only employee in the company.
</details>

<details>
<summary>96. Unique Binary Search Trees </summary>
Given n, how many structurally unique BST's (binary search trees) that store values 1 ... n?

Example:

Input: 3
Output: 5
Explanation:
Given n = 3, there are a total of 5 unique BST's:

    1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
</details>

<details>
<summary>834. Sum of Distances in Tree</summary>
An undirected, connected tree with N nodes labelled 0...N-1 and N-1 edges are given.

The ith edge connects nodes edges[i][0] and edges[i][1] together.

Return a list ans, where ans[i] is the sum of the distances between node i and all other nodes.

Example 1:

Input: N = 6, edges = [[0,1],[0,2],[2,3],[2,4],[2,5]]
Output: [8,12,6,10,10,10]
Explanation: 
Here is a diagram of the given tree:
  0
 / \
1   2
   /|\
  3 4 5
We can see that dist(0,1) + dist(0,2) + dist(0,3) + dist(0,4) + dist(0,5)
equals 1 + 1 + 2 + 2 + 2 = 8.  Hence, answer[0] = 8, and so on.
</details>

<details>
<summary>337. House Robber III </summary>
The thief has found himself a new place for his thievery again. There is only one entrance to this area, called the "root." Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that "all houses in this place forms a binary tree". It will automatically contact the police if two directly-linked houses were broken into on the same night.

Determine the maximum amount of money the thief can rob tonight without alerting the police.

Example 1:

Input: [3,2,3,null,3,null,1]

     3
    / \
   2   3
    \   \ 
     3   1

Output: 7 
Explanation: Maximum amount of money the thief can rob = 3 + 3 + 1 = 7.
</details>

<details>
<summary>450. Delete Node in a BST</summary>
Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return the root node reference (possibly updated) of the BST.

Basically, the deletion can be divided into two stages:

Search for a node to remove.
If the node is found, delete the node.
Note: Time complexity should be O(height of tree).
</details>
