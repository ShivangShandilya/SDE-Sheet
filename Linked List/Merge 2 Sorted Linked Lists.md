Problem - [Merge 2 Sorted Linked Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

-  Given two singly linked lists that are sorted in increasing order of node values, merge two sorted linked lists and return them as a sorted list. The list should be made by splicing together the nodes of the first two lists.

- Example 1:

      Input Format :
      l1 = {3,7,10}, l2 = {1,2,5,8,10}

      Output :
      {1,2,3,5,7,8,10,10}
     
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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if(list1 == null) return list2;
        if(list2 == null) return list1;
        
        ListNode newHead = null;
        ListNode current = null;
        
        if(list1.val <= list2.val){
            current = list1;
            newHead = current;
            list1 = list1.next;
        }else{
            current = list2;
            newHead = current;
            list2 = list2.next;
        }
        
        while(list1 != null && list2 != null) {
            if(list1.val <= list2.val) {
                current.next = list1;
                current = list1;
                list1 = list1.next;
                    
            }else{
                current.next = list2;
                current = list2;
                list2= list2.next;
            }
        }
        
        if(list1 == null) current.next = list2;
        if(list2 == null) current.next = list1;
        
        return newHead;
        
    }
}
```
