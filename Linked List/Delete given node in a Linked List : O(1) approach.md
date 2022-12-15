Problem - [Delete given node in a Linked List : O(1) approach](https://leetcode.com/problems/delete-node-in-a-linked-list/)

- Write a function to delete a node in a singly-linked list. You will not be given access to the head of the list instead, you will be given access to the node to be deleted directly. It is guaranteed that the node to be deleted is not a tail node in the list.

- Example 1:
 
      Input:
      Linked list: [1,4,2,3]
      Node = 2
      
      Output:
      Linked list: [1,4,3]
      
Explanation: Access is given to node 2. After deleting nodes, the linked list will be modified to [1,4,3].

- Example 2:
      
      Input:
      Linked list: [1,2,3,4]
      Node = 1
      
      Output:
      Linked list: [2,3,4]
      
Explanation: Access is given to node 1. After deleting nodes, the linked list will be modified to [2,3,4].
 
- Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public void deleteNode(ListNode node) {
        // Since we know input node is not last node, so nextNode will not be null
        ListNode nextNode = node.next;
        // Step 2
        node.val = nextNode.val;
        // Step 3
        node.next = nextNode.next;
        nextNode.next = null;
    }
}
```
