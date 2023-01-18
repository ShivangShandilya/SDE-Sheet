Problem - [Morris Inorder Traversal of a Binary tree](https://leetcode.com/problems/binary-tree-inorder-traversal/)

- Write a program for Morris Inorder Traversal of a Binary Tree.

- Example:

      Input:
      
     <img src = "https://user-images.githubusercontent.com/101946115/213114849-7e65271b-b6e0-4df1-8e33-e2cd2dc41c08.png" height = 300 width = 600 />
     
      Output: Inorder Traversal of this binary tree will be:- 4,2,5,6,1,3

- Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

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
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        helper(root, res);
        return res;
    }

    public void helper(TreeNode root, List<Integer> res) {
        if (root != null) {
            helper(root.left, res);
            res.add(root.val);
            helper(root.right, res);
        }
    }
}
```
