Problem - [Area of largest rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)

- Given an array of integers heights representing the histogram’s bar height where the width of each bar is 1  return the area of the largest rectangle in histogram.

- Example:

      Input: N =6, heights[] = {2,1,5,6,2,3}
 
      Output: 10

Explanation:

![image](https://user-images.githubusercontent.com/101946115/209967689-9187dd0d-34db-4b35-bb78-fdfbb56ee4b0.png)

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    static int largestRectangleArea(int histo[]) {
        Stack < Integer > st = new Stack < > ();
        int maxA = 0;
        int n = histo.length;
        for (int i = 0; i <= n; i++) {
            while (!st.empty() && (i == n || histo[st.peek()] >= histo[i])) {
                int height = histo[st.peek()];
                st.pop();
                int width;
                if (st.empty())
                    width = i;
                else
                    width = i - st.peek() - 1;
                maxA = Math.max(maxA, width * height);
            }
            st.push(i);
        }
        return maxA;
    }
}
```
