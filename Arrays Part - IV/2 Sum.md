Problem - [2 SUM](https://leetcode.com/problems/two-sum/)

- Given an array of integers nums[] and an integer target, return indices of the two numbers such that their sum is equal to the target.

<b>Note</b>: Assume that there is exactly one solution, and you are not allowed to use the same element twice. Example: If target is equal to 6 and num[1] = 3, then nums[1] + nums[1] = target is not a solution.

- Example 1:

      Input: nums = [2,7,11,15], target = 9

      Output: [0,1]

Explanation: Because nums[0] + nums[1] == 9, 
which is the required target, we return 
indexes [0,1]. (0-based indexing)

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] indices = new int[2];
        for(int i = 0; i < nums.length - 1; i++){
            for(int j = i + 1; j < nums.length; j++)
                if(nums[i] + nums[j] == target){
                    indices[0] = i;
                    indices[1] = j;
                }
        }
        return indices;
    }
}
```
