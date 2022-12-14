Problem - [Find the Middle of Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

- Given the head of a singly linked list, return the middle node of the linked list. If there are two middle nodes, return the second middle node.

Examples:

    Input Format: 
    ( Pointer / Access to the head of a Linked list )
    head = [1,2,3,4,5]

    Result: [3,4,5]
    ( As we will return the middle of Linked list the further linked list will be still available )

Explanation: The middle node of the list is node 3 as in the below image.

<p align = "center">
  <img src = "https://user-images.githubusercontent.com/101946115/207510032-0de09a6b-a963-459b-8b3d-5e1aa90e95d3.png" />
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
    public ListNode middleNode(ListNode head) {
        ListNode s=head;
        ListNode f=head;
        
        while(f!=null && f.next!=null){
            s=s.next;
            f=f.next.next;
        }
        return s;
    }
}
```
