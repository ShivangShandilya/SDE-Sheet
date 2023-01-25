Problem - [Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

- Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.

Example 1:

![image](https://user-images.githubusercontent.com/101946115/214466557-c8c91f32-2c81-472e-854e-084b56a11111.png)

    Input: nums = [-10,-3,0,5,9]
    Output: [0,-3,9,-10,null,5]

Explanation: [0,-10,5,null,-3,null,9] is also accepted:

![image](https://user-images.githubusercontent.com/101946115/214466632-cf766b0e-0c67-47b6-9a65-264d5037820b.png)

- SOLUTION:

```
/*int*
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        if(nums == null || nums.length == 0){
            return null;
        }
        return constructBSTrecursive(nums, 0, nums.length-1);
    }
    
    private TreeNode constructBSTrecursive(int[] nums, int left, int right){
         if(left > right){
             return null;
         }
        int mid = left + (right-left)/2;
        
        TreeNode current = new TreeNode(nums[mid]);
        current.left = constructBSTrecursive(nums,left,mid-1);
        current.right = constructBSTrecursive(nums,mid+1,right);
        return current;
    }
}
```
