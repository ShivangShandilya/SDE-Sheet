Problem - [Sort an array of 0s,1s and 2s](https://leetcode.com/problems/sort-colors/)

- Given an array consisting of only 0s, 1s and 2s. Write a program to in-place sort the array without using inbuilt sort functions. ( Expected: Single pass-O(N) and constant space)

- Example 1:

       Input: nums = [2,0,2,1,1,0]
       Output: [0,0,1,1,2,2]

       Input: nums = [2,0,1]
       Output: [0,1,2]

       Input: nums = [0]
       Output: [0]
       

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.


```
class Solution {
    public void sortColors(int[] nums) {
        int n = nums.length;
        int lo = 0;
        int mid = 0;
        int hi = n - 1;
        while(mid <= hi){
        switch(nums[mid]){
            case 0 : {
                int temp = nums[mid];
                nums[mid] = nums[lo];
                nums[lo] = temp;
                lo++;
                mid++;
                break;
            }
            case 1: {
                mid++;
                break;
            }
            case 2: {
                int temp = nums[mid];
                nums[mid] = nums[hi];
                nums[hi] = temp;
                hi--;
                break;
            }
        }
        }
    }
}

```
