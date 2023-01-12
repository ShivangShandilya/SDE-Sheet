Problem - [Post-Order Traversal Of Binary Tree](https://leetcode.com/problems/binary-tree-postorder-traversal/)

-  Postorder Traversal of a binary tree. Write a program for the postorder traversal of a binary tree.

Example:

<img src = "https://user-images.githubusercontent.com/101946115/212011493-70e285eb-0a5f-46b2-aab9-c986b980dac1.png" height = 300 width = 600 />

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
    public List<Integer> postorderTraversal(TreeNode root) {
    LinkedList<Integer> result = new LinkedList<>();
    Deque<TreeNode> stack = new ArrayDeque<>();
    TreeNode p = root;
    while(!stack.isEmpty() || p != null) {
        if(p != null) {
            stack.push(p);
            result.addFirst(p.val);  
            p = p.right;             
        } else {
            TreeNode node = stack.pop();
            p = node.left;           
        }
    }
    return result;
}
}
```

