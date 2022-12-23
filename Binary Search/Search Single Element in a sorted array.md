Problem - [Search Single Element in a sorted array](https://leetcode.com/problems/single-element-in-a-sorted-array/)

- Given a sorted array of N integers, where every element except one appears exactly twice and one element appears only once. Search Single Element in a sorted array.

- Example 1:

      Input: N = 9, array[] = {1,1,2,3,3,4,4,8,8} 

      Output: 2

Explanation: Every element in this sorted array except 2 
appears twice, therefore the answer returned will be 2.

- Example 2:

      Input: N = 7, array[] = {11,22,22,34,34,57,57} 

      Output: 11

Explanation: Every element in this sorted array except 
11 appears twice, therefore the answer returned will be 11.

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public int singleNonDuplicate(int[] nums) {
        int low = 0, high = nums.length-2;
        while(low <= high){
            int mid = (low + high) >> 1;
            if(nums[mid] == nums[mid^1])
                low = mid + 1;
            else
                high = mid - 1;
        }
        return nums[low];
    }
}
```
