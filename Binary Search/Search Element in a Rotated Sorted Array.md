Problem - [Search Element in a Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

- There is an integer array nums sorted in ascending order (with distinct values). Given the array nums after the possible clockwise rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums. We need to search a given element in a rotated sorted array.

- Example 1:

      Input: nums = [4,5,6,7,0,1,2,3], target = 0

      Output: 4

Explanation: Here, the target is 0. We can see that 0 is present in the given rotated sorted array, nums. Thus, we get output as 4, which is the index at which 0 is present in the array.

- Example 2:

      Input: nums = [4,5,6,7,0,1,2], target = 3

      Output: -1 

Explanation: Here, the target is 3. Since 3 is not present in the given rotated sorted array. Thus, we get output as -1.

Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public int search(int[] arr, int target) {
        int low = 0; 
        int high = arr.length-1;
        while(low <= high){
            int mid = (low + high) >> 1;
            
            if(arr[mid] == target)
                return mid;
            
            //to check if left side is sorted or not
            
            if(arr[low] <= arr[mid]){
                 //to check if our element lies in left half or not
                if(target >= arr[low] && target <= arr[mid])
                    high = mid - 1;
                else
                    low = mid + 1;
            }
            // to check if element lies in right half or not
            else{
                if(target <= arr[high] && target >= arr[mid])
                    low = mid + 1;
                else
                    high = mid - 1;
            }
        }
        return -1;
    }
}
```
