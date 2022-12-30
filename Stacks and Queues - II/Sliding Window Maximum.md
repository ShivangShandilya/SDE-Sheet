Problem - [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)

- Given an array of integers arr, there is a sliding window of size k which is moving from the very left of the array to the very right. You can only see the k numbers in the window. Each time the sliding window moves right by one position. Return the max sliding window.

- Example 1:

      Input: arr = [4,0,-1,3,5,3,6,8], k = 3

      Output: [4,3,5,5,6,8]

Explanation: 

![image](https://user-images.githubusercontent.com/101946115/210092800-9f25ac49-93ed-422b-9de5-334ffb0bb630.png)


For each window of size k=3, we find the maximum element in the window and add it to our output array.

- Example 2:

      Input: arr = [20,25], k = 2

      Output: [25]

Explanation: There’s just one window is size 2 that is possible and the maximum of the two elements is our answer.

- Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
   public static int[] maxSlidingWindow(int[] a, int k) {
        int n = a.length;
        int[] r = new int[n - k + 1];
        int ri = 0;
        // store index
        Deque < Integer > q = new ArrayDeque < > ();
        for (int i = 0; i < a.length; i++) {
            // remove numbers out of range k
            if (!q.isEmpty() && q.peek() == i - k) {
                q.poll();
            }
            // remove smaller numbers in k range as they are useless
            while (!q.isEmpty() && a[q.peekLast()] < a[i]) {
                q.pollLast();
            }

            q.offer(i);
            if (i >= k - 1) {
                r[ri++] = a[q.peek()];
            }
        }
        return r;
    }
}
```
