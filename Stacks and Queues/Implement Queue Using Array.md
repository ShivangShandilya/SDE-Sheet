Problem - [Implement Queue Using Array](https://www.codingninjas.com/codestudio/problems/2099908?topList=striver-sde-sheet-problems&utm_source=striver&utm_medium=website)

- Implement Queue Data Structure using Array with all functions like pop, push, top, size, etc.

- Example:

      Input: push(4)
             push(14)
             push(24)
             push(34)
             top()
             size()
             pop()

      Output: 

      The element pushed is 4
      The element pushed is 14
      The element pushed is 24
      The element pushed is 34
      The peek of the queue before deleting any element 4
      The size of the queue before deletion 4
      The first element to be deleted 4
      The peek of the queue after deleting an element 14
      The size of the queue after deleting an element 3
      
- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
/*
    Time Complexity : O(q)
    Space Complexity : O(q)

    Where q is the number of queries.
*/

public class Queue {
    int qfront, rear, size, queueSize;
    int[] q;

    Queue() {

        // Intialise the queue with 0 elements.
        rear = 0;
        qfront = 0;
        size = 0;
        queueSize = 100010;
        q = new int[100010];
    }

    // Function to check if the queue is empty.
    boolean isEmpty() {
        if (qfront == rear) {
            return true;
        }
        return false;
    }

    void enqueue(int data) {

        // Push the current element in the queue.
        q[rear] = data;
        rear = rear + 1;

        // Increase the value of size.
        size++;
    }

    int dequeue() {

        // Check if the queue is empty.
        if (isEmpty()) {
            return -1;
        }

        int ans = q[qfront];
        qfront++;
        size--;
        if (qfront == rear) {
            qfront = 0;
            rear = 0;
        }
        return ans;
    }

    int front() {

        // Check if the queue is empty.
        if (isEmpty()) {
            return -1;
        }

        // Return the element at front.
        return q[qfront];
    }

}

```
