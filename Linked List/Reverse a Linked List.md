Problem - [Reverse a Linked List](https://leetcode.com/problems/reverse-linked-list/)

- Given the head of a singly linked list, write a program to reverse the linked list, and return the head pointer to the reversed list.

Examples:

    Input Format: 
    head = [3,6,8,10]
    This means the given linked list is 3->6->8->10 with head pointer at node 3.
    
    Result:
    Output = [10,6,8,3]
    This means, after reversal, the list should be 10->6->8->3 with the head pointer at node 10.
    
 <p align = "center">
<img src = "https://user-images.githubusercontent.com/101946115/207509346-f0a553ef-9d31-4b1c-a38d-ad511ecc483c.png" height = 300 width = 900 />
 </p>
 
 This is how a linked list looks for a given input. the head is a reference that points to the initial or starting node of the list. To reverse it, we need to invert the linking between nodes. That is, node D should point to node C, node C to node B, and node B to node A. Then the head points to node D and node A has NULL.

<p align = "center">
  <img src = "https://user-images.githubusercontent.com/101946115/207509538-6c1093ed-f199-4c65-b206-3de534dace05.png" height = 300 width = 900 />
  </p>
 
 - Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
   public ListNode reverseList(ListNode head) {
       ListNode newHead = null;
       
       while(head != null){
           ListNode next = head.next;
           head.next = newHead;
           newHead = head;
           head = next;
       }
       return newHead;
    }
}
```
  
