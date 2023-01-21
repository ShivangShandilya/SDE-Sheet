Problem - [Check if the Binary Tree is Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)

- Check whether the given Binary Tree is a Balanced Binary Tree or not. A binary tree is balanced if, for all nodes in the tree, the difference between left and right subtree height is not more than 1.

Examples:

    Input Format: Given the root of Binary Tree
   
  <img src = "https://user-images.githubusercontent.com/101946115/213848113-4a5e427e-df28-4ed1-b776-a710097decaa.png" height = 400 width = 500 />
 
    Result: False

Explanation: At Node 4, Left Height = 1 & Right Height = 3, Absolute Difference is 2 which is greater than 1, Hence, not a balanced tree.

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
    public boolean isBalanced(TreeNode root) {
        return dfsHeight(root)!= - 1;
    }
    int dfsHeight(TreeNode root){
        if(root == null)return 0;
        
        int lh = dfsHeight(root.left);
        if(lh == -1)return -1;
        int rh = dfsHeight(root.right);
        if(rh == -1)return -1;
        
        if(Math.abs(lh - rh) > 1)return -1;
        return Math.max(lh, rh) + 1;
    }
}
```
