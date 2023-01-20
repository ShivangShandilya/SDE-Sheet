Problem - [Maximum depth of a Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

- Find the Maximum Depth of Binary Tree. Maximum Depth is the count of nodes of the longest path from the root node to the leaf node.

Examples:

    Input Format: Given the root of Binary Tree
    
<img src = "https://user-images.githubusercontent.com/101946115/213682060-24b3c48f-42f0-425e-b316-b28cd1fa596f.png" height = 400 />
 
    Result: 4

Explanation: Maximum Depth in this tree is 4 if we follow path 5 – 1 – 3 – 8 or 5 – 1 – 3 – 11

- SOLUTION:

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
    public int maxDepth(TreeNode root) {
        if(root==null){
             return 0;
        }
        int lheight = maxDepth(root.left);
        int rheight = maxDepth(root.right);
        if(lheight > rheight){
            return (lheight+1);
        }
        else{
            return (rheight+1);
        }
    
    }
}
```
