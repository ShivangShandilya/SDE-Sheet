Problem - [Largest Subarray with 0 sum](https://practice.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1)

-  Given an array containing both positive and negative integers, we have to find the length of the longest subarray with the sum of all elements equal to zero.

- Example 1:

      Input Format: N = 6, array[] = {9, -3, 3, -1, 6, -5}

      Result: 5

Explanation: The following subarrays sum to zero:
{-3, 3} , {-1, 6, -5}, {-3, 3, -1, 6, -5}
Since we require the length of the longest subarray, our answer is 5!

- Example 2:

      Input Format: N = 8, array[] = {6, -2, 2, -8, 1, 7, 4, -10}

      Result: 8

Subarrays with sum 0 : {-2, 2}, {-8, 1, 7}, {-2, 2, -8, 1, 7}, {6, -2, 2, -8, 1, 7, 4, -10}
Length of longest subarray = 8

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
int maxLen(int A[], int n)
    {
        // Your code here
        HashMap<Integer, Integer> mpp = new HashMap<Integer, Integer>();

        int maxi = 0;
        int sum = 0; 

        for(int i = 0;i<n;i++) {

            sum += A[i]; 

            if(sum == 0) {
                maxi = i + 1; 
            }
            else {
                if(mpp.get(sum) != null) {

                    maxi = Math.max(maxi, i - mpp.get(sum)); 
                }
                else {

                    mpp.put(sum, i); 
                }
            }
        }
        return maxi; 
    }
    ```
