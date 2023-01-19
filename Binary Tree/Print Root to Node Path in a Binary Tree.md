Problem - [Print Root to Node Path in a Binary Tree](https://www.interviewbit.com/problems/path-to-given-node/)

- We are given a binary tree T and a node V. We need to print a path from the root of the tree to the node.

Note:

- No two nodes in the tree have the same data value.
- It is assured that the node V is present and a path always exists.

Examples:

<img src = "https://user-images.githubusercontent.com/101946115/213524162-68d5dff3-42b6-4e83-9d20-9b0b61cb356a.png" height = 300 weight = 600/>

<img src = "https://user-images.githubusercontent.com/101946115/213524273-809e9ae1-2625-4d84-9aa0-61b929f12b17.png" height = 300 weight = 600/>

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

Pre-req: Traversal Techniques & Recursion

- Solution :

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
public class TUF {
    static boolean getPath(Node root, ArrayList < Integer > arr, int x) {
        // if root is NULL
        // there is no path
        if (root == null)
            return false;

        // push the node's value in 'arr'
        arr.add(root.data);

        // if it is the required node
        // return true
        if (root.data == x)
            return true;

        // else check whether the required node lies
        // in the left subtree or right subtree of
        // the current node
        if (getPath(root.left, arr, x) ||
            getPath(root.right, arr, x))
            return true;

        // required node does not lie either in the
        // left or right subtree of the current node
        // Thus, remove current node's value from
        // 'arr'and then return false   
        arr.remove(arr.size() - 1);
        return false;
    }

    public static void main(String args[]) {

        Node root = new Node(1);
        root.left = new Node(2);
        root.left.left = new Node(4);
        root.left.right = new Node(5);
        root.left.right.left = new Node(6);
        root.left.right.right = new Node(7);
        root.right = new Node(3);

        ArrayList < Integer > arr = new ArrayList < > ();

        boolean res;
        res = getPath(root, arr, 7);

        System.out.print("The path is ");
        for (int it: arr) {
            System.out.print(it + " ");
        }

    }
}
```
