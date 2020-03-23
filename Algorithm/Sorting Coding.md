## Sorting Coding

### JAVA releted
```
private class IntervalComparator implements Comparator<int[]> {
    @Override
    public int compare(int[] a, int[] b) {
        return a[0] < b[0] ? -1 : a[0] == b[0] ? 0 : 1;
    }
}
//OR
list.sort(new Comparator<Integer>() {
            public int compare(Integer o1, Integer o2) {
                if(o1>o2)
                    return 1;//第二个元素（o1）比第一个元素（o2）大，返回1
                if(o1==o2)
                    return 0;
                return -1;
            }//1,0,-1三者同时出现时，1表示不交换位置，0表示相等时不交换，-1表示交换
        });
//OR
Arrays.sort(intervals, (int[] i1, int[] i2) -> i1[0] != i2[0] ? i1[0] - i2[0] : i1[1] - i2[1]);
```
Increasing order: 
```
if(o1<o2)  return -1; //exchange
if(o1==o2)  return 0; //the same as return 1；return -1, the same element may exchange（it will influence map）
if(o1>o2)  return 1; //no change
```
Decreasing order:
```
if(o1>o2)  return -1;
if(o1==o2)  return 0;
if(o1<o2)  return 1;
```
`this.compareTo(that)`
```
returns 
a negative int if this < that
0 if this == that
a positive int if this > that
```
TreeMap<>
default: decreasing
```
Map<Integer, Double> map = new TreeMap<>();
TreeMap<Integer,Integer> map2= new TreeMap<Integer,Integer>(new Comparator<Integer>(){
            public int compare(Integer a,Integer b){
                return b-a;            
                });
for(Double sec: map.values()){}
for(Double sec: map.keySet()){}
for (Map.Entry<String,String> entry : gfg.entrySet())  
    System.out.println("Key = " + entry.getKey() + 
                 ", Value = " + entry.getValue()); 
```
PriorityQueue<>
default Min Heap:  that is the top element is the minimum one in the heap. 
```
PriorityQueue<Integer> q = new PriorityQueue<>(
    (n1, n2) -> map.get(n1) - map.get(n2)
); //min-heap
q.offer(i);
if(q.size() > k){
    q.poll();
}
```
ArrayList
```
list.addLast()
list.addFirst()
list.reverse()
```
* compare(Integer o1, Integer o2){}中，o1代表的是List容器中的后一个元素，o2代表的是List容器中的前一个元素！

### Leetcode

\#| Title|Difficulty|--
--|--|--|--
56  |  Merge Intervals  |  Medium|Intervals
253   | Meeting Rooms II  |  Medium|Intervals
280   |  Wiggle Sort |      Medium|
324   | Wiggle Sort II  |  Medium  |
522    |Longest Uncommon Subsequence II    |Medium  |
329| Longest Increasing Path in a Matrix|Hard|
524| Longest Word in Dictionary through Deleting|Medium|
506    |Relative Ranks   | Easy|
853   | Car Fleet   | Medium|
360| Sort Transformed Array|Medium|
315| Count of Smaller Numbers After Self|Hard|
 274| H-Index|Medium|
 692| Top K Frequent Words|Medium |Top K 
215   | Kth Largest Element in an Array    |Medium|Top K 
 347     |  Top K Frequent Elements    |   Sorting|Top K 
 658    |    Find K Closest Elements    |    Medium|Top K 
 373  |  Find K Pairs with Smallest Sums  |  Medium|Top K 
 
<details>
<summary>56. Merge Intervals</summary>
Given a collection of intervals, merge all overlapping intervals.<br>Input: [[1,3],[2,6],[8,10],[15,18]]<br>
Output: [[1,6],[8,10],[15,18]]<br>
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
</details>

<details>
<summary>253. Meeting Rooms II</summary>
Given an array of meeting time intervals consisting of start and end times [[s1,e1],[s2,e2],...] (si < ei), find the minimum number of conference rooms required.
Input: intervals = [(0,30),(5,10),(15,20)]
Output: 2
Explanation:
We need two meeting rooms
room1: (0,30)
room2: (5,10),(15,20)
</details>

<details>
<summary>280. Wiggle Sort</summary>
Given an unsorted array nums, reorder it in-place such that nums[0] <= nums[1] >= nums[2] <= nums[3]....
<br>Input: [3, 5, 2, 1, 6, 4]
<br>Output: [1, 6, 2, 5, 3, 4]
<br>Explanation: This question may have multiple answers, and [2, 6, 1, 5, 3, 4] is also ok.
</details>

<details>
<summary>324. Wiggle Sort II</summary>
<br>Given an unsorted array nums, reorder it such that nums[0] < nums[1] > nums[2] < nums[3]....
<br>Input: nums = [1, 5, 1, 1, 6, 4]
<br>Output: One possible answer is [1, 4, 1, 5, 1, 6].
</details>

<details>
<summary>522. Longest Uncommon Subsequence II</summary>
Given a list of strings, you need to find the longest uncommon subsequence among them. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings.

<br>A subsequence is a sequence that can be derived from one sequence by deleting some characters without changing the order of the remaining elements. Trivially, any string is a subsequence of itself and an empty string is a subsequence of any string.

<br>The input will be a list of strings, and the output needs to be the length of the longest uncommon subsequence. If the longest uncommon subsequence doesn't exist, return -1.

<br>Input: "aba", "cdc", "eae"
<br>Output: 3
</details>

<details>
<summary>329. Longest Increasing Path in a Matrix</summary>
Given an integer matrix, find the length of the longest increasing path.

From each cell, you can either move to four directions: left, right, up or down. You may NOT move diagonally or move outside of the boundary (i.e. wrap-around is not allowed).

Example 1:

Input: nums = 
[
  [9,9,4],
  [6,6,8],
  [2,1,1]
] 
Output: 4 
Explanation: The longest increasing path is [1, 2, 6, 9].

Example 2:

Input: nums = 
[
  [3,4,5],
  [3,2,6],
  [2,2,1]
] 
Output: 4 
Explanation: The longest increasing path is [3, 4, 5, 6]. Moving diagonally is not allowed.
</details>

<details>
<summary>524. Longest Word in Dictionary through Deleting</summary>
Given a string and a string dictionary, find the longest string in the dictionary that can be formed by deleting some characters of the given string. If there are more than one possible results, return the longest word with the smallest lexicographical order. If there is no possible result, return the empty string.

Example 1:
Input:
s = "abpcplea", d = ["ale","apple","monkey","plea"]

Output: 
"apple"

Example 2:
Input:
s = "abpcplea", d = ["a","b","c"]

Output: 
"a"
</details>

<details>
<summary>506. Relative Ranks</summary>
Given scores of N athletes, find their relative ranks and the people with the top three highest scores, who will be awarded medals: "Gold Medal", "Silver Medal" and "Bronze Medal".
<br>Example 1:
<br>Input: [5, 4, 3, 2, 1]
<br>Output: ["Gold Medal", "Silver Medal", "Bronze Medal", "4", "5"]
<br>Explanation: The first three athletes got the top three highest scores, so they got "Gold Medal", "Silver Medal" and "Bronze Medal".  For the left two athletes, you just need to output their relative ranks according to their scores.
</details>

<details>
<summary>853. Car Fleet</summary>
N cars are going to the same destination along a one lane road.  The destination is target miles away.
Each car i has a constant speed speed[i] (in miles per hour), and initial position position[i] miles towards the target along the road.
A car can never pass another car ahead of it, but it can catch up to it, and drive bumper to bumper at the same speed.
The distance between these two cars is ignored - they are assumed to have the same position.
A car fleet is some non-empty set of cars driving at the same position and same speed.  Note that a single car is also a car fleet.
If a car catches up to a car fleet right at the destination point, it will still be considered as one car fleet.
How many car fleets will arrive at the destination?
</details>

<details>
<summary>360. Sort Transformed Array</summary>
Given a sorted array of integers nums and integer values a, b and c. Apply a function of the form f(x) = ax2 + bx + c to each element x in the array.

The returned array must be in sorted order.

Expected time complexity: O(n)

Example:

nums = [-4, -2, 2, 4], a = 1, b = 3, c = 5,

Result: [3, 9, 15, 33]

nums = [-4, -2, 2, 4], a = -1, b = 3, c = 5

Result: [-23, -5, 1, 7]

</details>

<details>
<summary>315. Count of Smaller Numbers After Self</summary>
You are given an integer array nums and you have to return a new counts array. The counts array has the property where counts[i] is the number of smaller elements to the right of nums[i].

Example:

Input: [5,2,6,1]
Output: [2,1,1,0] 
Explanation:
To the right of 5 there are 2 smaller elements (2 and 1).
To the right of 2 there is only 1 smaller element (1).
To the right of 6 there is 1 smaller element (1).
To the right of 1 there is 0 smaller element.
</details>

<details>
<summary>274. H-Index</summary>
Given an array of citations (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.

According to the definition of h-index on Wikipedia: "A scientist has index h if h of his/her N papers have at least h citations each, and the other N − h papers have no more than h citations each."

Example:

Input: citations = [3,0,6,1,5]
Output: 3 
Explanation: [3,0,6,1,5] means the researcher has 5 papers in total and each of them had 
             received 3, 0, 6, 1, 5 citations respectively. 
             Since the researcher has 3 papers with at least 3 citations each and the remaining 
             two with no more than 3 citations each, her h-index is 3.
</details>


<details>
<summary>692. Top K Frequent Words</summary>
Given a non-empty list of words, return the k most frequent elements.

Your answer should be sorted by frequency from highest to lowest. If two words have the same frequency, then the word with the lower alphabetical order comes first.

Example 1:
Input: ["i", "love", "leetcode", "i", "love", "coding"], k = 2
<br>Output: ["i", "love"]
<br>Explanation: "i" and "love" are the two most frequent words.
    Note that "i" comes before "love" due to a lower alphabetical order.
    
Example 2:
<br>Input: ["the", "day", "is", "sunny", "the", "the", "the", "sunny", "is", "is"], k = 4
<br>Output: ["the", "is", "sunny", "day"]
<br>Explanation: "the", "is", "sunny" and "day" are the four most frequent words,
    with the number of occurrence being 4, 3, 2 and 1 respectively.
</details>



<details>
<summary>215. Kth Largest Element in an Array</summary>
Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.
<br>Example 1:
<br>Input: [3,2,1,5,6,4] and k = 2
<br>Output: 5
</details>

<details>
<summary>347. Top K Frequent Elements</summary>
Given a non-empty array of integers, return the k most frequent elements.

Example 1:

Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
</details>

<details>
<summary>658. Find K Closest Elements </summary>
Given a sorted array, two integers k and x, find the k closest elements to x in the array. The result should also be sorted in ascending order. If there is a tie, the smaller elements are always preferred.

Example 1:
Input: [1,2,3,4,5], k=4, x=3
Output: [1,2,3,4]
Example 2:
Input: [1,2,3,4,5], k=4, x=-1
Output: [1,2,3,4]
</details>

<details>
<summary>373. Find K Pairs with Smallest Sums</summary>
You are given two integer arrays nums1 and nums2 sorted in ascending order and an integer k.

Define a pair (u,v) which consists of one element from the first array and one element from the second array.

Find the k pairs (u1,v1),(u2,v2) ...(uk,vk) with the smallest sums.

Example 1:

Input: nums1 = [1,7,11], nums2 = [2,4,6], k = 3
Output: [[1,2],[1,4],[1,6]] 
Explanation: The first 3 pairs are returned from the sequence: 
             [1,2],[1,4],[1,6],[7,2],[7,4],[11,2],[7,6],[11,4],[11,6]
Example 2:

Input: nums1 = [1,1,2], nums2 = [1,2,3], k = 2
Output: [1,1],[1,1]
Explanation: The first 2 pairs are returned from the sequence: 
             [1,1],[1,1],[1,2],[2,1],[1,2],[2,2],[1,3],[1,3],[2,3]
</details>
