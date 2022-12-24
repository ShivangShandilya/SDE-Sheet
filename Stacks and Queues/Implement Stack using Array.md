Problem - [Implement Stack using Array](https://www.codingninjas.com/codestudio/problems/stack-implementation-using-array_3210209)

- Implement a stack using an array.

Note: Stack is a data structure that follows the Last In First Out (LIFO) rule.

Example:

<img src = "https://user-images.githubusercontent.com/101946115/209451273-29f3008a-339c-466f-845e-4a438a702242.png" height = 400 width = 600 />

Explanation: 
<b>
  
push(): Insert the element in the stack.

pop(): Remove and return the topmost element of the stack.

top(): Return the topmost element of the stack

size(): Return the number of remaining elements in the stack.
</b>
  
- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
/*
    Time complexity: O(1)
    Space complexity: O(N)
    
    Where 'N' is the capacity of the stack.
*/
import java.util.ArrayList;

public class Stack {
    // Declare array.
    ArrayList<Integer> myStack;

    // Stack size.
    int stackSize;

    // Maximum size.
    int n;

    // Constructor function.
    Stack(int n) {

        // Initialize class objects.
        myStack = new ArrayList<Integer>(n);
        for (int i = 0; i < n; i++) {
            myStack.add(0);
        }
        stackSize = -1;
        this.n = n;
    }

    // Push function.
    void push(int num) {

        // Check if stack is not full.
        if (stackSize != n - 1) {

            // Increment stack size and update array.
            ++stackSize;
            myStack.set(stackSize, num);
        }
    }

    // Pop function.
    int pop() {

        // Check if stack is not empty.
        if (stackSize != -1) {

            // Decrease size and return element.
            --stackSize;
            return myStack.get(stackSize + 1);
        } else {
            return -1;
        }
    }

    // Top function.
    int top() {

        // Check if stack is not empty.
        if (stackSize != -1) {

            // Return element.
            return myStack.get(stackSize);
        } else {
            return -1;
        }
    }

    // To check whether stack is empty or not.
    int isEmpty() {

        // Check if stack is not empty.
        if (stackSize != -1) {

            // Return element.
            return 0;
        } else {
            return 1;
        }
    }

    // To check whether stack is full or not.
    int isFull() {

        // Check if stack is not empty.
        if (stackSize != n - 1) {

            // Return element.
            return 0;
        } else {
            return 1;
        }
    }
}

```

