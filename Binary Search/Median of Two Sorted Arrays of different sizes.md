Problem - [Median of Two Sorted Arrays of different sizes](https://leetcode.com/problems/median-of-two-sorted-arrays/)

-  Given two sorted arrays arr1 and arr2 of size m and n respectively, return the median of the two sorted arrays.

Example 1:

    Input format: arr1 = [1,4,7,10,12], arr2 = [2,3,6,15]

    Output format : 6.00000

Explanation:

Merge both arrays. Final sorted array is [1,2,3,4,6,7,10,12,15]. We know that to find the median we find the mid element. Since, the size of the element is odd. By formula, the median will be at [(n+1)/2]th position of the final sorted array. Thus, for this example, the median is at [(9+1)/2]th position which is [5]th = 6.

- Example 2:

      Input: arr1 = [1], arr2 = [2]

      Output format:
      1.50000

Explanation:
 
Merge both arrays. Final sorted array is [1,2]. We know that to find the median we find the mid element. Since, the size of the element is even. By formula, the median will be the mean of elements at [n/2]th and  [(n/2)+1]th position of the final sorted array. Thus, for this example, the median is (1+2)/2 = 3/2 = 1.50000.

- Solution:

```
class Solution {
static double median(int arr1[],int arr2[],int m,int n) {
    if(m>n)
        return median(arr2,arr1,n,m);//ensuring that binary search happens on minimum size array
        
    int low=0,high=m,medianPos=((m+n)+1)/2;
    while(low<=high) {
        int cut1 = (low+high)>>1;
        int cut2 = medianPos - cut1;
        
        int l1 = (cut1 == 0)? Integer.MIN_VALUE:arr1[cut1-1];
        int l2 = (cut2 == 0)? Integer.MIN_VALUE:arr2[cut2-1];
        int r1 = (cut1 == m)? Integer.MAX_VALUE:arr1[cut1];
        int r2 = (cut2 == n)? Integer.MAX_VALUE:arr2[cut2];
        
        if(l1<=r2 && l2<=r1) {
            if((m+n)%2 != 0)
                return Math.max(l1,l2);
            else 
                return (Math.max(l1,l2)+Math.min(r1,r2))/2.0;
        }
        else if(l1>r2) high = cut1-1;
        else low = cut1+1;
    }
    return 0.0;
}
    
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
       int m = nums1.length;
        int n = nums2.length;
        
        return median(nums1, nums2, m, n);
    }
}
```
