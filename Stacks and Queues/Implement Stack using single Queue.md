Problem - [Implement Stack using single Queue](https://leetcode.com/problems/implement-stack-using-queues/)

- Implement a Stack using a single Queue.

Note: Stack is a data structure that follows the Last In First Out (LIFO) rule.

Note: Queue is a data structure that follows the First In First Out (FIFO) rule.

Example:

<img src = "https://user-images.githubusercontent.com/101946115/209803344-ca637656-5fb6-41ab-8a33-6a4afccc22f6.png" height = 400 width = 600 />

Explanation: 

- push(): Insert the element in the stack.

- pop(): Remove and return the topmost element of the stack.

- top(): Return the topmost element of the stack

- size(): Return the size of the stack

Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class MyStack {

    private Queue<Integer> queue = new LinkedList<>();

    public void push(int x) {
        queue.add(x);
        for (int i=1; i<queue.size(); i++)
            queue.add(queue.remove());
    }

    public int pop() {
       return queue.remove();
    }

    public int top() {
        return queue.peek();
    }

    public boolean empty() {
        return queue.isEmpty();
    }
}

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack obj = new MyStack();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.top();
 * boolean param_4 = obj.empty();
 */
 ```
