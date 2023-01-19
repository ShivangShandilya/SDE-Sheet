Problem - [Vertical Order Traversal of Binary Tree](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)

- Write a program for Vertical Order Traversal order of a Binary Tree.

Example:

<img src = "https://user-images.githubusercontent.com/101946115/213523623-0402b334-b554-482e-8b9f-da9c461f72bd.png" height = 300 weight = 600 />

- Problem Description:

Vertical Order Traversal, as the name suggests is a traversal in which we divide the binary tree in verticals from left to right, and in every vertical, we print the nodes from top to bottom.

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
    int min=0, max=0;
    Map<Integer, List<Integer>> map = new HashMap();
    public List<List<Integer>> verticalTraversal(TreeNode root) {
        List<List<Integer>> res = new ArrayList();
        if(root==null) return res;
        Queue<TreeNode> qt = new LinkedList();
        Queue<Integer> qi = new LinkedList();
        qt.add(root);
        qi.add(0);//not root.val
        while(!qt.isEmpty()){
            int size = qt.size();
            Map<Integer,List<Integer>> tmp = new HashMap();
            for(int i=0;i<size;i++){
                TreeNode cur = qt.poll();
                int idx = qi.poll();
                if(!tmp.containsKey(idx)) tmp.put(idx, new ArrayList<Integer>());
                tmp.get(idx).add(cur.val);
                if(idx<min)  min = idx;
                if(idx>max)  max = idx;
                if(cur.left!=null){
                    qt.add(cur.left);
                    qi.add(idx-1);
                }
                if(cur.right!=null){
                    qt.add(cur.right);
                    qi.add(idx+1);
                } 
            }
            for(int key : tmp.keySet()){
                if(!map.containsKey(key)) map.put(key, new ArrayList<Integer>());
                List<Integer> list = tmp.get(key);
                Collections.sort(list);
                map.get(key).addAll(list);
            }
            
        }
        for (int i=min; i<=max; i++){
            List<Integer> list = map.get(i);
            res.add(list);
        }
        return res;
    }
}

```
