Problem - [Longest Common Subsequence](https://leetcode.com/problems/longest-consecutive-sequence/)

- You are given an array of ‘N’ integers. You need to find the length of the longest sequence which contains the consecutive elements.

- Example 1:

      Input: [100, 200, 1, 3, 2, 4]

      Output: 4

Explanation: The longest consecutive subsequence is 1, 2, 3, and 4.

- Example 2:

      Input: [3, 8, 5, 7, 6]

      Output: 4

Explanation: The longest consecutive subsequence is 5, 6, 7, and 8.

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public int longestConsecutive(int[] nums) {
        
        HashSet<Integer> set = new HashSet<>();
        for(int num : nums){
            set.add(num);
        }
        
        int longestStreak = 0;
        
        for(int num : nums){
            if(!set.contains(num - 1)){
                int currentNum = num;
                int currentStreak = 1;
                
                while(set.contains(currentNum + 1)){
                    currentNum += 1;
                    currentStreak += 1;
                }
             longestStreak = Math.max(longestStreak, currentStreak);
            }
        }
        return longestStreak;
    }
}
```
