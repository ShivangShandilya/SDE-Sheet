Problem - [Top view of a Binary Tree](https://practice.geeksforgeeks.org/problems/top-view-of-binary-tree/1)

- Given below is a binary tree. The task is to print the top view of the binary tree. The top view of a binary tree is the set of nodes visible when the tree is viewed from the top.

- Example 1:

      Input: 
  ![image](https://user-images.githubusercontent.com/101946115/213522654-db020319-d75e-45cc-a966-9966eee2949d.png)

      Output: 2 1 3

- Solution:

```
class Solution
{
    //Function to return a list of nodes visible from the top view 
    //from left to right in Binary Tree.
    static ArrayList<Integer> topView(Node root)
    {
        ArrayList<Integer> ans = new ArrayList<>(); 
        if(root == null) return ans;
        Map<Integer, Integer> map = new TreeMap<>();
        Queue<Pair> q = new LinkedList<Pair>();
        q.add(new Pair(root, 0)); 
        while(!q.isEmpty()) {
            Pair it = q.remove();
            int hd = it.hd; 
            Node temp = it.node; 
            if(map.get(hd) == null) map.put(hd, temp.data); 
            if(temp.left != null) {
                
                q.add(new Pair(temp.left, hd - 1)); 
            }
            if(temp.right != null) {
                
                q.add(new Pair(temp.right, hd + 1)); 
            }
        }
    
        for (Map.Entry<Integer,Integer> entry : map.entrySet()) {
            ans.add(entry.getValue()); 
        }
        return ans; 
        
    }
}
```
