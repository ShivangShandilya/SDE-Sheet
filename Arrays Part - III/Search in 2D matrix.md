Problem - [Search in 2D matrix](https://leetcode.com/problems/search-a-2d-matrix/)

-  Given an m*n 2D matrix and an integer, write a program to find if the given integer exists in the matrix.

Given matrix has the following properties:

Integers in each row are sorted from left to right.

The first integer of each row is greater than the last integer of the previous row

- Example 1:

      Input: matrix = 
             [[1,3,5,7],
             [10,11,16,20],
             [23,30,34,60]], 

target = 3

       Output: true

Explanation: As the given integer(target) exists in the given 2D matrix, the function has returned true.

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if(matrix.length == 0)return false;
        
        int n = matrix.length;
        int m = matrix[0].length;
        
        int lo = 0;
        int hi = (n * m) - 1;
        
        while(lo <= hi){
            int mid = (lo + (hi - lo)/2);
            if(matrix[mid / m][mid % m] == target)
                return true;
            
            if(matrix[mid / m][mid % m] < target)
                lo = mid + 1;
            
            else
                hi = mid - 1;

        }
        return false;
    }
}
```
