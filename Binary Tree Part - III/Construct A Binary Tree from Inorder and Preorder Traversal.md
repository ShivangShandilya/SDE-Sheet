Problem - [Construct A Binary Tree from Inorder and Preorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

- Given the Inorder and Preorder Traversal of a binary tree, we need to construct the unique binary tree represented by them.

Example:

<img src = "https://user-images.githubusercontent.com/101946115/213947035-31eb9850-0fac-46b3-9a25-81c12bd85703.png" height = 300 width = 600 />

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
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        Map<Integer,Integer> map = new HashMap<>();
        for(int i = 0; i < inorder.length; i++){
            map.put(inorder[i],i);
        }
        TreeNode root = buildTree(preorder, 0 , preorder.length - 1,inorder, 0, inorder.length - 1, map);
        
        return root;
    }
    
    public TreeNode buildTree(int[] preorder, int preStart, int preEnd, int[] inorder, int inStart, int inEnd, Map<Integer,Integer> map){
            if(preStart > preEnd || inStart > inEnd)return null;
        
        TreeNode root = new TreeNode(preorder[preStart]);
        int inRoot = map.get(root.val);
        int numsLeft = inRoot - inStart;
        
        root.left = buildTree(preorder, preStart + 1 , preStart + numsLeft ,inorder, inStart, inRoot - 1, map);
        root.right = buildTree(preorder, preStart + numsLeft + 1 , preEnd ,inorder, inRoot + 1, inEnd , map);
        
        return root;
        }
}
```
