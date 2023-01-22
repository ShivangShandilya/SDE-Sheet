Problem - [Check for Children Sum Property in a Binary Tree](https://www.codingninjas.com/codestudio/problems/childrensumproperty_790723?topList=striver-sde-sheet-problems&utm_source=striver&utm_medium=website)

- Write a program that converts any binary tree to one that follows the children sum property.

The children sum property is defined as, For every node of the tree, the value of a node is equal to the sum of values of its children(left child and right child).

Note: 

- The node values can be increased by 1 any number of times but decrement of any node value is not allowed.

- A value for a NULL node can be assumed as 0.

- You are not allowed to change the structure of the given binary tree.

Example:

<img src = "https://user-images.githubusercontent.com/101946115/213947302-96c8af4c-ee21-47b4-a41f-3cf15f2ef819.png" height = 300 width = 600 />

Pre-req: Tree Traversals

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

Solution :

```
import java.util.*;
class Node {
  int data;
  Node  left,  right;
  Node(int data)
  {
      this.data=data;
      left=null;
      right=null;
  }
}
class TUF{
static void reorder(Node  root) {
  if (root == null) return;
  int child = 0;
  if (root . left!=null) {
    child += root . left . data;
  }
  if (root . right!=null) {
    child += root . right . data;
  }

  if (child < root . data) {
    if (root . left!=null) root . left . data = root . data;
    else if (root . right!=null) root . right . data = root . data;
  }

  reorder(root . left);
  reorder(root . right);

  int tot = 0;
  if (root . left!=null) tot += root . left . data;
  if (root . right!=null) tot += root . right . data;
  if (root . left!=null || root . right!=null) root . data = tot;
}
static void changeTree(Node  root) {
  reorder(root);
}

public static void main(String args[]) {

  Node  root = new Node(2);
  root . left = new Node(35);
  root . left . left = new Node(2);
  root . left . right = new Node(3);
  root . right = new Node(10);
  root . right . left = new Node(5);
  root . right . right = new Node(2);

  changeTree(root);

}
}
```
