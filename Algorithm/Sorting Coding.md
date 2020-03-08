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
```
PriorityQueue<Integer> q = new PriorityQueue<>(
    (n1, n2) -> map.get(n1) - map.get(n2)
);
q.offer(i);
if(q.size() > k){
    q.poll();
}
```
* compare(Integer o1, Integer o2){}中，o1代表的是List容器中的后一个元素，o2代表的是List容器中的前一个元素！

### Leetcode

\#| Title|Difficulty
--|--|--
56  |  Merge Intervals  |  Medium
280   |  Wiggle Sort |      Medium
324   | Wiggle Sort II  |  Medium  
527   |  Word Abbreviation    | Hard
253   | Meeting Rooms II  |  Medium
215   | Kth Largest Element in an Array    |Medium
522    |Longest Uncommon Subsequence II    |Medium  
506    |Relative Ranks   | Easy
853   | Car Fleet   | Medium
347     |  Top K Frequent Elements    |   Sorting

<details>
<summary>56. Merge Intervals</summary>
Given a collection of intervals, merge all overlapping intervals.<br>Input: [[1,3],[2,6],[8,10],[15,18]]<br>
Output: [[1,6],[8,10],[15,18]]<br>
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
</details>

[link](https://leetcode.com/problems/merge-intervals/)

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
<summary>527. Word Abbreviation</summary>
Given an array of n distinct non-empty strings, you need to generate minimal possible abbreviations for every word following rules below.
<br>1. Begin with the first character and then the number of characters abbreviated, which followed by the last character.
<br>2. If there are any conflict, that is more than one words share the same abbreviation, a longer prefix is used instead of only the first character until making the map from word to abbreviation become unique. In other words, a final abbreviation cannot map to more than one original words.
<br> 3. If the abbreviation doesn't make the word shorter, then keep it as original.
<br>Input: ["like","god","internal","me","internet","interval","intension","face","intrusion"]
<br>Output: ["l2e","god","internal","me","i6t","interval","inte4n","f2e","intr4n"]
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
<summary>215. Kth Largest Element in an Array</summary>
Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.
<br>Example 1:
<br>Input: [3,2,1,5,6,4] and k = 2
<br>Output: 5
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
<summary>347. Top K Frequent Elements</summary>
Given a non-empty array of integers, return the k most frequent elements.

Example 1:

Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
</details>
