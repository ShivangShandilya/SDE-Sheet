Problem - [Maximum Sum Path in Binary Tree](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

- Write a program to find the maximum sum path in a binary tree. A path in a binary tree is a sequence of nodes where every adjacent pair of nodes are connected by an edge. A node can only appear in the sequence at most once. A path need not pass from the root. We need to find the path with the maximum sum in the binary tree.

Example:

    Input:

<img src = "https://user-images.githubusercontent.com/101946115/213946954-c7cfd902-b054-4511-ab2e-62b2c9492c5d.png" height = 300 width = 600 />

    Output: The Max Path Sum for the Tree is 42

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

Solution:

```
/**
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
    public int maxPathSum(TreeNode root) {
        int[] maxValue = new int[1];
        maxValue[0] = Integer.MIN_VALUE;
        maxPathDown(root,maxValue);
        return maxValue[0];
    }
    
    public int maxPathDown(TreeNode node, int[] maxValue){
        if(node == null)return 0;
        
        int left = Math.max(0 , maxPathDown(node.left, maxValue));
        int right = Math.max(0 , maxPathDown(node.right, maxValue));
        
        maxValue[0] = Math.max(maxValue[0], left + right + node.val);
        return Math.max(left,right) + node.val;
    }
}
```
