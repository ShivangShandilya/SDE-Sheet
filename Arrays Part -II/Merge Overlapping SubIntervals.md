Problem - [Merge Overlapping Sub-Intervals](https://leetcode.com/problems/merge-intervals/)

- Given an array of intervals, merge all the overlapping intervals and return an array of non-overlapping intervals.

- Example 1

      Input: intervals=[[1,3],[2,6],[8,10],[15,18]]

      Output: [[1,6],[8,10],[15,18]]

Explanation: Since intervals [1,3] and [2,6] are overlapping we can merge them to form [1,6]
 intervals.
 
- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.


```
class Solution {
    public int[][] merge(int[][] intervals) {
        List<int[]>res = new ArrayList<>();
        
        if(intervals.length == 0 || intervals == null)
            return res.toArray(new int[0][]);
        
        Arrays.sort(intervals, (a,b) -> a[0] - b[0]);
        
        int start = intervals[0][0];
        int end = intervals[0][1];
        
        for(int[] i : intervals){
            if(i[0] <= end)
                end = Math.max(end,i[1]);
            
            else{
                res.add(new int[]{start, end});
                start = i[0];
                end = i[1];
            }
        }
        res.add(new int[]{start, end});
        return res.toArray(new int[0][]);
    }
}
```
