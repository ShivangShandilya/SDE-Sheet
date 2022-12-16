Problem - [Starting point of loop in a Linked List](https://leetcode.com/problems/linked-list-cycle-ii/)

- Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return null.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that the tail’s next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.

Do not modify the linked list.

- Example 1:
 
      Input:
      head = [1,2,3,4,3,6,10]

      Output:
      tail connects to node index 2

Explanation:

<img src = "https://user-images.githubusercontent.com/101946115/208021471-e24224b7-2e5f-4167-99fe-3f64f0af5034.png" height = 300 width = 900 />

- Solution

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
    public ListNode detectCycle(ListNode head) {
       if(head == null || head.next == null) return null;
        ListNode slow = head;
        ListNode fast = head;
        ListNode entry = head;
        
        while(fast.next != null && fast.next.next != null){
            slow = slow.next;
            fast = fast.next.next;
            
            if(slow == fast){
                while(slow != entry){
                    slow = slow.next;
                    entry = entry.next;
                }
                return entry;
            }
        }
        return null;
    }
}
```



