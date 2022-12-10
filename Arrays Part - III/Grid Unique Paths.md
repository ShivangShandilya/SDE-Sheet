Problem - [Grid Unique Paths](https://leetcode.com/problems/unique-paths/)

- Given a matrix m X n, count paths from left-top to the right bottom of a matrix with the constraints that from each cell you can either only move to the rightward direction or the downward direction.

- Example 1:

      Input Format: m = 2, n= 2
      Output: 2
Explanation: From the top left corner there are total 2 ways to reach the bottom right corner:

Step 1: Right ->> Down


<img src= "https://user-images.githubusercontent.com/101946115/206870687-6b96501e-a7fd-4dbb-aefd-8edfdc2a1538.png" height = 200 weight = 200/>

Step 2: Down ->> Right


<img src = "https://user-images.githubusercontent.com/101946115/206870741-76b2df79-814a-4363-bac0-dab4a9f7c4a4.png" height = 200 weight = 200 />

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public int uniquePaths(int n, int m) {
    int[] prev = new int[m];          
      for(int i = 0; i < n; i++){
          int[] temp =  new int[m];
            for(int j = 0; j < m; j++){
                
                if(i == 0 && j == 0){
                    temp[j] = 1;
                    continue;
                }
                
                int up = 0;
                int left = 0;
                
                if(i > 0)
                 up += prev[j];
                
                if(j > 0)
                 left += temp[j - 1];
            
               temp[j] = up + left;
            }
          prev = temp;
        }
       
        return prev[m-1];
    }
}
```

