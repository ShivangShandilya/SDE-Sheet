Problem - [Implement Min Stack](https://leetcode.com/problems/min-stack/)

-  Implement Min Stack | O(2N) and O(N) Space Complexity. Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

- Examples:

      Input Format:["MinStack", "push", "push", "push", "getMin", "pop", "top", "getMin"]
      [
      [ ], [-2], [0], [-3], [ ], [ ], [ ], [ ]
      ]

      Result: [null, null, null, null, -3, null, 0, -2]

Explanation: 

stack < long long > st

st.push(-2); Push element in stack

st.push(0); Push element in stack

st.push(-3); Push element in stack

st.getMin(); Get minimum element fromstack

st.pop(); Pop the topmost element

st.top(); Top element is 0

st.getMin(); Minimum element is -2

- Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class MinStack {
    Stack < Long > st = new Stack < Long > ();
    Long mini;

    /** initialize your data structure here. */
    public MinStack() {
        mini = Long.MAX_VALUE;
    }

    public void push(int value) {
        Long val = Long.valueOf(value);
        if (st.isEmpty()) {
            mini = val;
            st.push(val);
        } else {
            if (val < mini) {
                st.push(2 * val - mini);
                mini = val;
            } else {
                st.push(val);
            }
        }
    }

    public void pop() {
        if (st.isEmpty()) return;

        Long val = st.pop();
        if (val < mini) {
            mini = 2 * mini - val;
        }
    }

    public int top() {
        Long val = st.peek();
        if (val < mini) {
            return mini.intValue();
        }
        return val.intValue();
    }

    public int getMin() {
        return mini.intValue();
    }
}
/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(val);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
 ```
