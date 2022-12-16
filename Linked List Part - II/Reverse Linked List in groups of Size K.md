Problem - [Reverse Linked List in groups of Size K](https://leetcode.com/problems/reverse-nodes-in-k-group/)

- Given the head of a linked list, reverse the nodes of the list k at a time, and return the modified list. k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should remain as it is.

- Example 1

      Input:
      head = [1,2,3,4,5,6,7,8] k=3

      Output:
      head = [3,2,1,6,5,4,7,8]

Explanation: 

![image](https://user-images.githubusercontent.com/101946115/208021001-b0a3fccf-6819-47f9-94e3-14986974a846.png)

- Solution

```
public ListNode reverseKGroup(ListNode head, int k) {
    ListNode curr = head;
    int count = 0;
    while (curr != null && count != k) { // find the k+1 node
        curr = curr.next;
        count++;
    }
    if (count == k) { // if k+1 node is found
        curr = reverseKGroup(curr, k); // reverse list with k+1 node as head
        // head - head-pointer to direct part, 
        // curr - head-pointer to reversed part;
        while (count-- > 0) { // reverse current k-group: 
            ListNode tmp = head.next; // tmp - next head in direct part
            head.next = curr; // preappending "direct" head to the reversed list 
            curr = head; // move head of reversed part to a new node
            head = tmp; // move "direct" head to the next node in direct part
        }
        head = curr;
    }
    return head;
}
```
