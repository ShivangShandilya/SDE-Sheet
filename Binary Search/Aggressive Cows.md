Problem - [Aggressive Cows](https://www.spoj.com/problems/AGGRCOW/)

- There is a new barn with N stalls and C cows. The stalls are located on a straight line at positions x1,….,xN (0 <= xi <= 1,000,000,000). We want to assign the cows to the stalls, such that the minimum distance between any two of them is as large as possible. What is the largest minimum distance?

Examples:

Input: No of stalls = 5 
       Array: {1,2,8,4,9}
       And number of cows: 3

Output: One integer, the largest minimum distance 3

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
import java.util.*;
class TUF {
    static boolean isPossible(int a[], int n, int cows, int minDist) {
        int cntCows = 1;
        int lastPlacedCow = a[0];
        for (int i = 1; i < n; i++) {
            if (a[i] - lastPlacedCow >= minDist) {
                cntCows++;
                lastPlacedCow = a[i];
            }
        }
        if (cntCows >= cows) return true;
        return false;
    }
    public static void main(String args[]) {
        int n = 5, cows = 3;
        int a[]={1,2,8,4,9};
        Arrays.sort(a);

        int low = 1, high = a[n - 1] - a[0];

        while (low <= high) {
            int mid = (low + high) >> 1;

            if (isPossible(a, n, cows, mid)) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        System.out.println("The largest minimum distance is " + high);


    }
}
```
