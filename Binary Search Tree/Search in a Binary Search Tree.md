Problem - [Search in a Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/description/)

- You are given the root of a binary search tree (BST) and an integer val.

Find the node in the BST that the node's value equals val and return the subtree rooted with that node. If such a node does not exist, return null.

Example 1:

![image](https://user-images.githubusercontent.com/101946115/214466314-4b7c5c1b-3dac-4f86-8f4c-317782386779.png)

    Input: root = [4,2,7,1,3], val = 2

    Output: [2,1,3]
    
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
    public TreeNode searchBST(TreeNode root, int val) {
        while(root!=null && root.val!=val){
            root = val < root.val ? root.left : root.right;
        }
        return root;
    }
}
```
