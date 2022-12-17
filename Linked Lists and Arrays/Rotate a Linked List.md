Problem - [Rotate a Linked List](https://leetcode.com/problems/rotate-list/description/)

- Given the head of a linked list, rotate the list to the right by k places.

- Example 1:

      Input:
	    head = [1,2,3,4,5] 
	    k = 2
      
      Output:
      head = [4,5,1,2,3]
      
Explanation:
 We have to rotate the list to the right twice.
 
<img src = "https://user-images.githubusercontent.com/101946115/208231221-f8afeacd-db6c-4e82-ab7b-8134f4bd670d.png" height = 300 width = 700 />

- Solution

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
    public ListNode rotateRight(ListNode head, int k) {
        // any multiple of k is gonna give us our original linked list
        //edge cases
        if(head == null || head.next == null || k==0)return head;
        
        //compute the length
        ListNode cur = head;
        int len = 1;
        while(cur.next != null){
            len++;
            cur=cur.next;
        }
        
        //go till that node
        cur.next = head;  //we connect last to head making it a circular linked list
        k = k % len;
        k = len - k;
        while(k-- > 0) cur = cur.next; //to reach len - k node
        
        //make tht node head and break connection
        head = cur.next;
        cur.next = null;
        
        return head;
    }
}
```
