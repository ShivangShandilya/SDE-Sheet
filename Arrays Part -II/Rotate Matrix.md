Problem - [Rotate Matrix](https://leetcode.com/problems/rotate-image/)

- You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

- Example 1:

![image](https://user-images.githubusercontent.com/101946115/206114673-bbc94a48-6d5b-4018-8ece-81f701380d2d.png)

     Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
     Output: [[7,4,1],[8,5,2],[9,6,3]]


- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.


```
class Solution {
    public void rotate(int[][] matrix) {
        for(int i = 0;i < matrix.length; i++){
            for(int j = i; j < matrix[0].length; j++){
                int temp = 0;
                temp = matrix[i][j];   // here we have transposed first and then we are gng to reverse it to get the desired result
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        for(int i = 0; i < matrix.length; i++){
            for(int j = 0; j < matrix.length/2; j++){
                int temp = 0;
                temp = matrix[i][j];
                matrix[i][j] = matrix[i][matrix.length-1-j];  // here we reversed every row
                matrix[i][matrix.length-1-j] = temp;
            }
        }
    }
}
```
