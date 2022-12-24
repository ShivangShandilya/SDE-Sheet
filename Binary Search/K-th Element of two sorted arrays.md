Problem - [K-th Element of two sorted arrays](https://practice.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1)

- Given two sorted arrays of size m and n respectively, you are tasked with finding the element that would be at the kth position of the final sorted array.

- Example 1:

      Input: m = 5
             n = 4
             array1 = [2,3,6,7,9]
             array2 = [1,4,8,10]
             k = 5

      Output:
       6

Explanation: Merging both arrays and sorted. Final array will be -
 [1,2,3,4,6,7,8,9,10]
We can see at k = 5 in the final array has 6. 

- Example 2:

      Input:
           m = 1
           n = 4
           array1 = [0]
           array2 = [1,4,8,10]
           k = 2

      Output:
       4

Explanation:
 Merging both arrays and sorted. Final array will be -
 [1,4,8,10]
 
We can see at k = 2 in the final array has 4

- Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
import java.util.*;
public class Main {
    static int kthelement(int array1[], int array2[], int m, int n, int k) {
        int p1 = 0, p2 = 0, counter = 0, answer = 0;

        while (p1 < m && p2 < n) {
            if (counter == k) break;
            else if (array1[p1] < array2[p2]) {
                answer = array1[p1];
                ++p1;
            } else {
                answer = array2[p2];
                ++p2;
            }
            ++counter;
        }
        if (counter != k) {
            if (p1 != m - 1)
                answer = array1[k - counter];
            else
                answer = array2[k - counter];
        }
        return answer;
    }
    public static void main(String args[]) {
        int array1[] = {2,3,6,7,9};
        int array2[] = {1,4,8,10};
        int m = array1.length;
        int n = array2.length;
        int k = 5;
        System.out.println("The element at the kth position in the final sorted array is "
        + kthelement(array1, array2, m, n, k));

    }
}
```

