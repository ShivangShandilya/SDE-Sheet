Problem - [Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

- Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”

- Example 1:

![image](https://user-images.githubusercontent.com/101946115/214684688-9ed2deb5-033d-466f-ad86-7c44fd9fe29f.png)

    Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
    Output: 6

Explanation: The LCA of nodes 2 and 8 is 6.

- SOLUTION

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
        if(root==null) return null;
        
        int curr = root.val;
        if(curr < p.val && curr < q.val)
            return lowestCommonAncestor(root.right,p,q);
        if(curr > p.val && curr > q.val)
            return lowestCommonAncestor(root.left,p,q);
        
        return root;
    }
}
```
