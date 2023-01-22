Problem - [Check for Symmetrical Binary Tree](https://leetcode.com/problems/symmetric-tree/)

- A symmetrical binary tree is a tree that forms a mirror of itself around the center. In other words, every node in the left subtree will have a mirror image in the right subtree.

Examples:

<img src = "https://user-images.githubusercontent.com/101946115/213947132-14140f54-29fb-4e6e-a167-a345497589dc.png" height = 300 width = 400 />

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

Pre-req: Tree Traversal

- Solution :

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
    public boolean isSymmetric(TreeNode root) {
    return root==null || isSymmetricHelp(root.left, root.right);
}

private boolean isSymmetricHelp(TreeNode left, TreeNode right){
    if(left==null || right==null)
        return left==right;
    if(left.val!=right.val)
        return false;
    return isSymmetricHelp(left.left, right.right) && isSymmetricHelp(left.right, right.left);
}
}
```
