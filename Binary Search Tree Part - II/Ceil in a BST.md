Problem - [Ceil in a BST](https://practice.geeksforgeeks.org/problems/implementing-ceil-in-bst/1)

- Given a BST and a number X, find Ceil of X.

Note: Ceil(X) is a number that is either equal to X or is immediately greater than X.

- Example 1:

      Input:
         5
       /   \
      1      7
       \
        2 
         \
          3

      X = 3

      Output: 3

Explanation: We find 3 in BST, so ceil
of 3 is 3.

- SOLUTION:

```
class Tree {

    // Function to return the ceil of given number in BST.

    int findCeil(Node root, int key) {

        if (root == null) return -1;

        // Code here

        int ans = -1;

        while(root != null){

            if(root.data==key) return root.data;

            else if(root.data>key){

                ans = root.data;

                root = root.left;

            }

            else root = root.right;

        }

        return ans;

    }
 }
```
  
