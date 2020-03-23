## LinkedList Coding

### JAVA releted
```
public class ListNode {
int val;
     ListNode next;
     ListNode(int x) { val = x; }
 }
```
### Leetcode

\#| Title|Difficulty
--|--|--
21|    Merge Two Sorted Lists  |  Easy
23 |   Merge k Sorted Lists  |  Hard    
382 |   Linked List Random Node |   Medium    
369   | Plus One Linked List  |  Medium    
82            |Remove Duplicates from Sorted List II | Medium
83            | Remove Duplicates from Sorted List | Easy

<details>
<summary>21. Merge 2 Sorted Lists </summary>
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

Example:

Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
</details>

<details>
<summary>23. Merge k Sorted Lists </summary>
Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

Example:

Input:
[
  1->4->5,
  1->3->4,
  2->6
]
Output: 1->1->2->3->4->4->5->6
</details>

<details>
<summary>382. Linked List Random Node</summary>
Given a singly linked list, return a random node's value from the linked list. Each node must have the same probability of being chosen.

Follow up:
What if the linked list is extremely large and its length is unknown to you? Could you solve this efficiently without using extra space?

Example:

// Init a singly linked list [1,2,3].
ListNode head = new ListNode(1);
head.next = new ListNode(2);
head.next.next = new ListNode(3);
Solution solution = new Solution(head);

// getRandom() should return either 1, 2, or 3 randomly. Each element should have equal probability of returning.
solution.getRandom();
</details>

<details>
<summary>369. Plus One Linked List</summary>
Given a non-negative number represented as a singly linked list of digits, plus one to the number.

The digits are stored such that the most significant digit is at the head of the list.

Example:
Input:
1->2->3

Output:
1->2->4
</details>

<details>
<summary>82. Remove Duplicates from Sorted List II</summary>
Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.

Return the linked list sorted as well.

Example 1:

Input: 1->2->3->3->4->4->5
Output: 1->2->5
Example 2:

Input: 1->1->1->2->3
Output: 2->3
</details>

<details>
<summary>83. Remove Duplicates from Sorted List</summary>
Given a sorted linked list, delete all duplicates such that each element appear only once.

Example 1:

Input: 1->1->2
Output: 1->2
Example 2:

Input: 1->1->2->3->3
Output: 1->2->3
</details>
