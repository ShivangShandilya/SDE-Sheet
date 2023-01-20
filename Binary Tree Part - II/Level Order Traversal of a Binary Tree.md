Problem - [Level Order Traversal of a Binary Tree](https://leetcode.com/problems/binary-tree-level-order-traversal/)

- Level order traversal of a binary tree. Given the root node of the tree and you have to print the value of the level of the node by level.

Example 1:

<img src = "https://user-images.githubusercontent.com/101946115/213681515-ef0b7005-7ba9-4a60-a257-c4419616c59a.png" height = 300 weight = 600 />

    Output:
    20 10 30 5 15 25 35
    
We will print the nodes of the first level (20), then we will print nodes of second level(10,30) and at last we will print nodes of the last level(5,15,25,35)

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
    public List<List<Integer>> levelOrder(TreeNode root) {
        Queue<TreeNode> q = new LinkedList<>();
        List<List<Integer>> wrapList = new LinkedList<>();
        if(root == null)return wrapList;
        q.offer(root);
        while(!q.isEmpty()){
            int levelNum = q.size();
            List<Integer> subList = new LinkedList<>();
            for(int i = 0 ;i < levelNum; i++){
                if(q.peek().left != null)q.offer(q.peek().left);
                if(q.peek().right != null)q.offer(q.peek().right);
                subList.add(q.poll().val); 
            }
            wrapList.add(subList);
        }
        return wrapList;
    }
}
```
