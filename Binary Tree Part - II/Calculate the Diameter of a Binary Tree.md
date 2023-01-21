Problem - [Calculate the Diameter of a Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)

- Find the Diameter of a Binary Tree. Diameter is the length of the longest path between any 2 nodes in the tree and this path may or may not pass from the root.

Example 1:

    Input Format: Given the root of Binary Tree
    
   ![image](https://user-images.githubusercontent.com/101946115/213847973-798ad0ea-ecf3-47f9-b3e4-238d1ead4694.png)
   
    Result: 4

Explanation: Longest Path available is 7 – 4 – 8 – 1 – 3 of length 4

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
    public int diameterOfBinaryTree(TreeNode root) {
        int[] diameter = new int[1];
        height(root, diameter);
        return diameter[0];
    }
    
    public int height(TreeNode node, int[] diameter){
        if(node == null)return 0;
        
        int lh = height(node.left,diameter);
        int rh = height(node.right,diameter);
        diameter[0] = Math.max(diameter[0],lh + rh);
        return 1 + Math.max(lh, rh);
    }
}
```
