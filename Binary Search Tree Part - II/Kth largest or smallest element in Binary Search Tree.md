Problem - [Kth largest/smallest element in Binary Search Tree](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

- Given a binary search tree find the kth largest and smallest element in Binary Search Tree.

Examples:
 
    Input: N=6
       Arr=[5,3,6,2,4,1]
       K=3

    Output: Kth largest element is 4
        Kth smallest element is 3
        

    Input: N=7
       Arr=[10,40,45,20,25,30,50]
       k=3

    Output: Kth largest element is 4
            Kth smallest element is 3

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
    public int kthSmallest(TreeNode root, int k) {
       LinkedList<TreeNode> stack = new LinkedList<>();
        
        while(true){
            while(root != null){
                stack.push(root);
                root = root.left;
            }
        
        root = stack.pop();
        if(--k == 0)return root.val;
        root = root.right;
         }
    }
}
```
