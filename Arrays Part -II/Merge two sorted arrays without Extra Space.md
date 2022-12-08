Problem - [Merge two sorted arrays without Extra Space](https://leetcode.com/problems/merge-sorted-array/)

- Given two sorted arrays arr1[] and arr2[] of sizes n and m in non-decreasing order. Merge them in sorted order. Modify arr1 so that it contains the first N elements and modify arr2 so that it contains the last M elements.

Example 1:

    Input: 
    n = 4, arr1[] = [1 4 8 10] 
    m = 5, arr2[] = [2 3 9]

    Output: 
    arr1[] = [1 2 3 4]
    arr2[] = [8 9 10]

Explanation:
After merging the two non-decreasing arrays, we get, 1,2,3,4,8,9,10.

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int p1 = m-1, p2 = n-1, i = m+n-1;
        while(p2>=0){
            if(p1>=0 && nums1[p1]>nums2[p2]){
                nums1[i--] = nums1[p1--];
            }
            else{
                nums1[i--] = nums2[p2--];
            }
        }
    }
}
```
