Problem - [Count Maximum Consecutive One’s in the array](https://leetcode.com/problems/max-consecutive-ones/)

- Given an array that contains only 1 and 0 return the count of maximum consecutive ones in the array.

- Example 1:

      Input: prices = {1, 1, 0, 1, 1, 1}

      Output: 3

Explanation: There are two consecutive 1’s and three consecutive 1’s in the array out of which maximum is 3.

- Example 2:

      Input: prices = {1, 0, 1, 1, 0, 1} 

      Output: 2

Explanation: There are two consecutive 1's in the array. 

- Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int count=0;
        int ans=0;
        for(int i=0;i<nums.length;i++){
            if(nums[i] == 1)
                count++;
        
            else{
                count=0;
            }
            ans=Math.max(ans,count);

    }
    return ans;
}
}
```
