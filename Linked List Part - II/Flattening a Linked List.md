Problem  - [Flattening a Linked List](https://practice.geeksforgeeks.org/problems/flattening-a-linked-list/1)

- Given a Linked List of size N, where every node represents a sub-linked-list and contains two pointers:

(i) a next pointer to the next node,

(ii) a bottom pointer to a linked list where this node is head.

Each of the sub-linked-list is in sorted order.

Flatten the Link List such that all the nodes appear in a single level while maintaining the sorted order. 

Note: The flattened list will be printed using the bottom pointer instead of the next pointer.

- Example 1:

      Input:
      Number of head nodes = 4
      Array holding length of each list with head and bottom = [4,2,3,4]
      Elements of entire linked list = [5,7,8,30,10,20,19,22,50,28,35,40,45]

<img src = "https://user-images.githubusercontent.com/101946115/208021761-5fa6ede8-d7e2-4094-8abd-738b30a0c51a.png" height = 400 width = 700 />

      Output:
      Flattened list = [5,7,8,10,19,20,22,28,30,35,40,45,50]
      
Explanation:
 Flattened list is the linked list consisting entire elements of the given list in sorted order
 
 - Solution

```
class TUF
{
    Node mergeTwoLists(Node a, Node b) {
        
        Node temp = new Node(0);
        Node res = temp; 
        
        while(a != null && b != null) {
            if(a.data < b.data) {
                temp.bottom = a; 
                temp = temp.bottom; 
                a = a.bottom; 
            }
            else {
                temp.bottom = b;
                temp = temp.bottom; 
                b = b.bottom; 
            }
        }
        
        if(a != null) temp.bottom = a; 
        else temp.bottom = b;
        return res.bottom; 
    
    }
    Node flatten(Node root)
    {
       
            if (root == null || root.next == null) 
                return root; 
      
            // recur for list on right 
            root.next = flatten(root.next); 
      
            // now merge 
            root = mergeTwoLists(root, root.next); 
      
            // return the root 
            // it will be in turn merged with its left 
            return root; 
    }
}
```
