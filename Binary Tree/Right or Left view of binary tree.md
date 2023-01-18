Problem - [Right/Left view of binary tree](https://practice.geeksforgeeks.org/problems/left-view-of-binary-tree/1)

-  Given a Binary Tree, find the Right/Left view of it. The right view of a Binary Tree is a set of nodes visible when the tree is viewed from the right side. The left view of a Binary Tree is a set of nodes visible when the tree is viewed from the left side.

- Example:

      Input:
     ![image](https://user-images.githubusercontent.com/101946115/213116168-c01c3741-fd2b-4681-849e-f5760b917a76.png)
       
      Output: Right view- 1 2
              Left view- 1 3
              
Explanation: Seeing through the left side it sees only 1 and 3 while through the right side we only see 1 and 2.


- Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
public class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> result = new ArrayList<Integer>();
        rightView(root, result, 0);
        return result;
    }
    
    public void rightView(TreeNode curr, List<Integer> result, int currDepth){
        if(curr == null){
            return;
        }
        if(currDepth == result.size()){
            result.add(curr.val);
        }
        
        rightView(curr.right, result, currDepth + 1);
        rightView(curr.left, result, currDepth + 1);
        
    }
}
```



