Problem - [Kadane's Algorithm](https://leetcode.com/problems/maximum-subarray/)

- Given an integer array arr, find the contiguous subarray (containing at least one number) which
has the largest sum and return its sum and print the subarray.

- Example 1:

      Input: arr = [-2,1,-3,4,-1,2,1,-5,4] 

      Output: 6 

Explanation: [4,-1,2,1] has the largest sum = 6. 

- Examples 2: 

      Input: arr = [1] 

      Output: 1 

Explanation: Array has only one element and which is giving positive sum of 1. 

-Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first. 

```
class Solution {
    public int maxSubArray(int[] nums) {
        int current_sum = nums[0];
        int max_so_far = nums[0];
        
        for(int i = 1; i < nums.length; i++){
            current_sum = Math.max(nums[i],current_sum + nums[i]);
            max_so_far = Math.max(current_sum , max_so_far);
        }
        return max_so_far;
    }
}
```
