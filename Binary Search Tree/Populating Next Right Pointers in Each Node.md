Problem - [Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

- You are given a perfect binary tree where all leaves are on the same level, and every parent has two children. The binary tree has the following definition:

```
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```

Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.

- Example 1:

<img src = "https://user-images.githubusercontent.com/101946115/214465779-69108a60-31d7-4418-bac2-2ac2e770572e.png" height = 300 width = 600 />

    Input: root = [1,2,3,4,5,6,7]

    Output: [1,#,2,3,#,4,5,6,7,#]

Explanation: Given the above perfect binary tree (Figure A), your function should populate each next pointer to point to its next right node, just like in Figure B. The serialized output is in level order as connected by the next pointers, with '#' signifying the end of each level.

- SOLUTION:

```
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;

    public Node() {}
    
    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, Node _left, Node _right, Node _next) {
        val = _val;
        left = _left;
        right = _right;
        next = _next;
    }
};
*/

class Solution {
    public Node connect(Node root) {
        dfs(root, null);        
        return root;
    }
    
    private void dfs(Node curr, Node next) {
        if (curr == null) return;
        curr.next = next;
        dfs(curr.left, curr.right);
        dfs(curr.right, curr.next == null ? null : curr.next.left);
    }
}
```



