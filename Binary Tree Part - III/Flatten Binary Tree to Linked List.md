Problem - [Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)

<b>Write a program that flattens a given binary tree to a linked list.</b>

Note: 

- The sequence of nodes in the linked list should be the same as that of the preorder traversal of the binary tree.

- The linked list nodes are the same binary tree nodes. You are not allowed to create extra nodes.

- The right child of a node points to the next node of the linked list whereas the left child points to NULL.

Example:

<img src = "https://user-images.githubusercontent.com/101946115/213947229-2ff4d635-ca2b-488b-8568-ca8c6d13f7f3.png" height = 300 width = 600 />

Pre-req: Traversal Techniques

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

- Solution:

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
static TreeNode prev = null;
    static void flatten(TreeNode root) {
        TreeNode cur = root;
		while (cur!=null)
		{
			if(cur.left!=null)
			{
				TreeNode pre = cur.left;
				while(pre.right!=null)
				{
					pre = pre.right;
				}
				pre.right = cur.right;
				cur.right = cur.left;
				cur.left = null;
			}
			cur = cur.right;
		}
    }
}
```
