Problem - [Add two numbers represented as Linked Lists](https://leetcode.com/problems/add-two-numbers/)

-  Given the heads of two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

- Example 1

      Input Format: 
      (Pointer/Access to the head of the two linked lists)

      num1  = 243, num2 = 564

      l1 = [2,4,3]
      l2 = [5,6,4]

      Result: sum = 807; L = [7,0,8]

Explanation: Since the digits are stored in reverse order, reverse the numbers first to get the or  original number and then add them as → 342 + 465 = 807. Refer to the image below.

![image](https://user-images.githubusercontent.com/101946115/207897190-a82d457e-a78a-41fc-b7a0-80f401b940f7.png)

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode();
        ListNode temp = dummy;
        int carry=0;
        while(l1 != null || l2 != null || carry == 1){
            int sum=0;
            if(l1!=null){
                sum+=l1.val;
                l1=l1.next;
            }
            if(l2!=null){
                sum+=l2.val;
                l2=l2.next;
            }
            sum+=carry;
            carry = sum/10;
            ListNode node = new ListNode(sum % 10);
            temp.next = node;
            temp = temp.next;
        }
        return dummy.next;
    }
}
```
