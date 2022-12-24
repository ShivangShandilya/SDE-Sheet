Problem - [Kth largest/smallest element in an array](https://leetcode.com/problems/kth-largest-element-in-an-array/)

- Given an unsorted array, print Kth Largest and Smallest Element from an unsorted array.

Examples:

- Example 1:

      Input: Array = [1,2,6,4,5,3] , K = 3 

      Output: kth largest element = 4, kth smallest element = 3

- Example 2:
 
      Input: Array = [1,2,6,4,5] , k = 3

      Output : kth largest element = 4,  kth smallest element = 4
      
- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.   

```
class Solution {
    public int findKthLargest(int[] nums, int k) {
	if (nums == null || nums.length == 0) return Integer.MAX_VALUE;
    return findKthLargest(nums, 0, nums.length - 1, nums.length - k);
}    

public int findKthLargest(int[] nums, int start, int end, int k) {// quick select: kth smallest
	if (start > end) return Integer.MAX_VALUE;
	
	int pivot = nums[end];// Take A[end] as the pivot, 
	int left = start;
	for (int i = start; i < end; i++) {
		if (nums[i] <= pivot) // Put numbers < pivot to pivot's left
			swap(nums, left++, i);			
	}
	swap(nums, left, end);// Finally, swap A[end] with A[left]
	
	if (left == k)// Found kth smallest number
		return nums[left];
	else if (left < k)// Check right part
		return findKthLargest(nums, left + 1, end, k);
	else // Check left part
		return findKthLargest(nums, start, left - 1, k);
} 

void swap(int[] A, int i, int j) {
	int tmp = A[i];
	A[i] = A[j];
	A[j] = tmp;				
}
}
```
