Problem - [Bottom view of a Binary Tree](https://practice.geeksforgeeks.org/problems/bottom-view-of-binary-tree/1)

- Given a binary tree, print the bottom view from left to right. A node is included in the bottom view if it can be seen when we look at the tree from the bottom.

- Example:

      Input:
     ![image](https://user-images.githubusercontent.com/101946115/213116742-e35ae0a8-7f31-4364-b63f-1869388fb98a.png)

      Output: 3 1 2

Explanation: 

If you look up from the bottom from left to right then first we get 3, then 1 and 2.

Disclaimer: Don’t jump directly to the solution, try it out yourself first

- Solution:

```
class Solution
{
    //Function to return a list containing the bottom view of the given tree.
    public ArrayList <Integer> bottomView(Node root)
    {
        ArrayList<Integer> ans = new ArrayList<>(); 
        if(root == null) return ans;
        Map<Integer, Integer> map = new TreeMap<>();
        Queue<Node> q = new LinkedList<Node>();
        root.hd = 0;
        q.add(root); 
        while(!q.isEmpty()) {
            Node temp = q.remove();
            int hd = temp.hd; 
            map.put(hd, temp.data); 
            if(temp.left != null) {
                temp.left.hd = hd - 1; 
                q.add(temp.left); 
            }
            if(temp.right != null) {
                temp.right.hd = hd + 1; 
                q.add(temp.right); 
            }
        }
        
        for (Map.Entry<Integer,Integer> entry : map.entrySet()) {
            ans.add(entry.getValue()); 
        }
        return ans; 
        
    }
}
```
