Problem - [Remove N-th node from the end of a Linked List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

- Given a linked list, and a number N. Find the Nth node from the end of this linked list and delete it. Return the head of the new modified linked list.

Example 1 : 

    Input: head = [1,2,3,4,5], n = 2

    Output: [1,2,3,5]

Explanation: Refer Below Image

![image](https://user-images.githubusercontent.com/101946115/207510837-27cd4a0a-7b8a-48d9-909b-f59cfcb57e5f.png)

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode start = new ListNode();   //making a dummy node
        start.next = head;          // dummy nodes next is head
        ListNode fast = start;       // we initialze fast and slow to dummy node
        ListNode slow = start;     

        for(int i = 1; i <= n; ++i)
            fast = fast.next;
    
        while(fast.next != null)
        {
            fast = fast.next;
            slow = slow.next;
        }
        
        slow.next = slow.next.next;
        
        return start.next;
    }
}
```
