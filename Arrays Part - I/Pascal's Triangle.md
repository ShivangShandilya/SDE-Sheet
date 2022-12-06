Problem - [Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)

- Given an integer N, return the first N rows of Pascal’s triangle.
- In Pascal’s triangle, each number is the sum of the two numbers directly above it as shown in the figure below:

![image](https://user-images.githubusercontent.com/101946115/205865985-a125afb5-ac1e-4187-9685-bbcfcf43f2ab.png)

- Example 1:

Input Format: N = 5

- Explanation: There are 5 rows in the output matrix. Each row corresponds to each one of the rows in the image shown above.

-Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<List<Integer>>();
        List<Integer> row ,pre=null;
        for(int i=0; i<numRows;i++){
            row = new ArrayList<Integer>();
            for(int j=0; j<=i;j++){
                if(j==0 || j==i){
                 row.add(1);
                }
                else{
                    row.add(pre.get(j-1)+pre.get(j));
                }
            }
            pre=row;
            res.add(row);
        }
        return res;
    }
}
```

