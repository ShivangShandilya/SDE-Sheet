Problem - [Morris Preorder Traversal of a Binary Tree](https://takeuforward.org/data-structure/morris-preorder-traversal-of-a-binary-tree/)

- Given a Binary Tree, find the Morris preorder traversal of Binary Tree.

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

- Solution:

```
import java.util.*;
class Node {
    int data;
    Node left, right;
    Node(int data) {
        this.data = data;
        left = null;
        right = null;
    }
}

public class Main {
    static ArrayList < Integer > preorderTraversal(Node root) {
        ArrayList < Integer > preorder = new ArrayList < > ();
        Node cur = root;
        while (cur != null) {
            if (cur.left == null) {
                preorder.add(cur.data);
                cur = cur.right;
            } else {
                Node prev = cur.left;
                while (prev.right != null && prev.right != cur) {
                    prev = prev.right;
                }

                if (prev.right == null) {
                    prev.right = cur;
                    preorder.add(cur.data);
                    cur = cur.left;
                } else {
                    prev.right = null;
                    cur = cur.right;
                }
            }
        }
        return preorder;
    }

    public static void main(String args[]) {

        Node root = new Node(1);
        root.left = new Node(2);
        root.right = new Node(3);
        root.left.left = new Node(4);
        root.left.right = new Node(5);
        root.left.right.right = new Node(6);

        ArrayList < Integer > preorder = new ArrayList < > ();
        preorder = preorderTraversal(root);

        System.out.println("The Preorder Traversal is: ");
        for (int i = 0; i < preorder.size(); i++) {
            System.out.print(preorder.get(i) + " ");
        }

    }
}
```
