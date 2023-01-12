Problem - [Preorder Traversal of Binary Tree](https://leetcode.com/problems/binary-tree-preorder-traversal/)

-  Given a binary tree print the preorder traversal of binary tree.

Example:

<img src="https://user-images.githubusercontent.com/101946115/212011009-5414436d-07ed-4cad-a2cb-c2ef4f6810b3.png" height = 300 width = 600 />

- Solution

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
    public List<Integer> preorderTraversal(TreeNode root) {
     List<Integer> res = new ArrayList<>();
        helper(root,res);
        return res;
    }
    private void helper(TreeNode root, List<Integer> res){
        if(root!=null){
            res.add(root.val);
            helper(root.left,res);
            helper(root.right,res);
        }
    }
}
```
