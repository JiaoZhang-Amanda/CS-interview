## Sorting Coding

### Leetcode

\#| Title|Difficulty
--|--|--
56  |  Merge Intervals  |  Medium
280   |    Wiggle Sort |      Medium
324   | Wiggle Sort II  |  Medium  
527   |  Word Abbreviation    | Hard
253   | Meeting Rooms II  |  Medium
215   | Kth Largest Element in an Array    |Medium
522    |Longest Uncommon Subsequence II    |Medium  
506    |Relative Ranks   | Easy
853   | Car Fleet   | Medium

<details>
<summary>56. Merge Intervals<br>Given a collection of intervals, merge all overlapping intervals.<br>Input: [[1,3],[2,6],[8,10],[15,18]]<br>
Output: [[1,6],[8,10],[15,18]]<br>
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].</summary>
<code>
class Solution {
    private class IntervalComparator implements Comparator<int[]> {
        @Override
        public int compare(int[] a, int[] b) {
            return a[0] < b[0] ? -1 : a[0] == b[0] ? 0 : 1;
        }
    }
    public int[][] merge(int[][] intervals) {
        int m = intervals.length;
        int count = 1;
        if(m <= 1) return intervals;
        Collections.sort(Arrays.asList(intervals), new IntervalComparator());
        for(int i = 1; i < m; i++){
            boolean canMerge = help(intervals[i], intervals[i-1]);
            if(canMerge){
                intervals[i][0] = Math.min(intervals[i][0], intervals[i-1][0]);
                intervals[i][1] = Math.max(intervals[i][1], intervals[i-1][1]);
                intervals[i-1] = null;
            }else count++;
        }
        int[][] res = new int[count][2];
        int j = 0;
        for(int i = 0; i < m; i++){
            if(intervals[i] != null){
                res[j++] = intervals[i];
            }
        }
        return res;
    }
    public boolean help(int[] a, int[] b){
        return Math.max(a[0], b[0]) <= Math.min(a[1], b[1]);
    }
}
</code>
</details>

<details>
<summary>280. Wiggle Sort</summary>
......
</details>
