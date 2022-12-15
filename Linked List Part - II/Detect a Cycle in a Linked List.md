Problem - [Detect a Cycle in a Linked List](https://leetcode.com/problems/linked-list-cycle/)

- Given head, the head of a linked list, determine if the linked list has a cycle in it. There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer.

Return true if there is a cycle in the linked list. Otherwise, return false.

- Example 1:

      Input:
      Head = [1,2,3,4]

      Output:
      true
      
Explanation: Here, we can see that we can reach node at position 1 again by following the next pointer. Thus, we return true for this case.

<img src = "https://user-images.githubusercontent.com/101946115/207900172-7e0ced52-230f-4334-892c-23f19087842e.png" height = 300 weight = 700 />

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        
        while(fast!=null && fast.next!=null){
            fast = fast.next.next;
            slow = slow.next;
            if(fast == slow){
                return true;
            }
        }
                    return false;

    }
}
```
