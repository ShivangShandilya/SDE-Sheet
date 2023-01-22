Problem - [Check if two trees are identical](https://leetcode.com/problems/same-tree/)

- Given two Binary Tree. Write a program to check if two trees are identical or not.

Example 1:

![image](https://user-images.githubusercontent.com/101946115/213905115-f6e00e83-fe94-4ad6-bf3c-5c24a67fac82.png)

    Input: p = [1,2,3], q = [1,2,3]
    Output: true
    
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
    public boolean isSameTree(TreeNode p, TreeNode q) {
           Queue<TreeNode> queue = new LinkedList<>();
        if (p == null && q == null)
            return true;
        else if (p == null || q == null)
            return false;
        if (p != null && q != null) {
            queue.offer(p);
            queue.offer(q);
        }
        while (!queue.isEmpty()) {
            TreeNode first = queue.poll();
            TreeNode second = queue.poll();
            if (first == null && second == null)
                continue;
            if (first == null || second == null)
                return false;
            if (first.val != second.val)
                return false;
            queue.offer(first.left);
            queue.offer(second.left);
            queue.offer(first.right);
            queue.offer(second.right);
        }
        return true;
    }
    
}
```
