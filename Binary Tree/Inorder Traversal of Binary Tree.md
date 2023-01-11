Problem - [Inorder Traversal of Binary Tree](https://leetcode.com/problems/binary-tree-inorder-traversal/)

- Given a Binary Tree. Find and print the inorder traversal of Binary Tree.

Examples:

    Input:

<img src = "https://user-images.githubusercontent.com/101946115/211836513-41bc5954-9e69-4367-b3a2-0abc496acb6b.png" height = 400 width = 700 />

    Output:  The inOrder Traversal is : 4 2 8 5 1 6 3 9 7 10 

- Solution

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

