Problem - [Find intersection of Two Linked List](https://leetcode.com/problems/intersection-of-two-linked-lists/)

- Given the heads of two singly linked-lists headA and headB, return the node at which the two lists intersect. If the two linked lists have no intersection at all, return null.

- Example 1:

      Input:
      List 1 = [1,3,1,2,4], List 2 = [3,2,4]

      Output:
      2
      
Explanation: Here, both lists intersecting nodes start from node 2.

<img src = "https://user-images.githubusercontent.com/101946115/207898888-80cd7c7c-3573-4a97-8c74-12e5d7f36c89.png" height = 300 weight = 700 />

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if(headA == null || headB == null)
            return null;
        
        ListNode a = headA;
        ListNode b = headB;
        
        while(a!=b){
            a = a == null? headB : a.next;
            b = b == null? headA : b.next;
        }
        return a;
    }
}
```
