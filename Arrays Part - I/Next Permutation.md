Problem - [Next Permutation](https://leetcode.com/problems/next-permutation)

- Given an array Arr[] of integers, rearrange the numbers of the given array into the lexicographically next greater permutation of numbers.
- If such an arrangement is not possible, it must rearrange it as the lowest possible order (i.e., sorted in ascending order).

- Example 1 :

          Input format: Arr[] = {1,3,2}

          Output: Arr[] = {2,1,3}

- Explanation: All permutations of {1,2,3} are {{1,2,3} , {1,3,2}, {2,13} , {2,3,1} , {3,1,2} , {3,2,1}}. So, the next permutation just after {1,3,2} is {2,1,3}.

-Solution

Disclamer:  Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public void nextPermutation(int[] nums) {
        if(nums == null || nums.length <= 1) return;  //base case
        int i = nums.length-2;  //our breakpoint can be at 2nd last index so we traverse from there
        while(i >= 0 && nums[i] >= nums[i+1]) i--;  // this checks for the condtion a[i] < a[i+1]
        //if the while loop comes out to be true then only if condition will execute
        if(i >= 0){
            int j = nums.length-1;
            while(nums[j] <= nums[i])j--; // this is the condition when a[index2] < a[index 1]
            swap(nums, i , j);   // here we then swap both indexes
        }
        reverse(nums, i+1 ,nums.length-1);
        }
    
    public void swap(int[] nums, int i, int j){
        int tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
    
    public void reverse(int[] nums, int i, int j){
        while(i < j) swap(nums, i++, j++);
    }
}

//Example for this is
// 1  3  5  4  2 

```
