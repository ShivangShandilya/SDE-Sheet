Problem - [Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)

- Given the root of a binary tree, flatten the tree into a "linked list":

The "linked list" should use the same TreeNode class where the right child pointer points to the next node in the list and the left child pointer is always null.

The "linked list" should be in the same order as a pre-order traversal of the binary tree.

- Example 1:

<img src = "https://user-images.githubusercontent.com/101946115/215353560-a0d969e2-c6d9-4bc0-bf64-af824757e5f2.png" height = 300 width = 600 />

    Input: root = [1,2,5,3,4,null,6]
    Output: [1,null,2,null,3,null,4,null,5,null,6]
    
- SOLUTION

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
