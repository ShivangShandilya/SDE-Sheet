Problem - [Lowest Common Ancestor for two given Nodes](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

- Given a binary tree, Find the Lowest Common Ancestor for two given Nodes (x,y).

Lowest Common Ancestor(LCA): The lowest common ancestor is defined between two nodes x and y as the lowest node in T that has both x and y as descendants (where we allow a node to be a descendant of itself.

Examples:

<img src = "https://user-images.githubusercontent.com/101946115/213905051-0e867292-cef1-45da-9eeb-d4a5390933c4.png" height = 300 width = 300 />

Example 1: 

    Input: x = 4 , y = 5

    Output: 2 

Explanation: All ancestors for 4,5 are 2,1.  But we need Lowest Common ancestor, So we will consider lowest and also common ancestor that is 2

- Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root == null || root == q || root == p)return root;
        
        TreeNode left = lowestCommonAncestor(root.left, p ,q);
        TreeNode right = lowestCommonAncestor(root.right, p , q);
        
        if(left == null)return right;
        else if(right == null)return left;
        else return root;
    }
}
```
