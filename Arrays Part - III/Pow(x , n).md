Problem - [Pow(x , n)](https://leetcode.com/problems/powx-n/)

- Given a double x and integer n, calculate x raised to power n. Basically Implement pow(x, n).

- Example 1:

      Input: x = 2.00000, n = 10

      Output: 1024.00000

Explanation: You need to calculate 2.00000 raised to 10 which gives ans 1024.00000

- Example 2:

      Input: x = 2.10000, n = 3

      Output: 9.26100

Explanation: You need to calculate 2.10000 raised to 3 which gives ans 9.26100

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public double myPow(double x, int n) {
        double ans = 1.0; //initializing the final ans
        long nn = n; //making a copy of n as in our algo n will be destroyed
        if(nn < 0) nn = -1 * nn;  //we check if its a -ve number and then we make it a +ve number
         while(nn > 0){
             if(nn % 2 == 1){  //we check if the power is even or odd
                 ans = ans * x;
                 nn = nn-1;
             }
             else{
                 x = x * x;
                 nn = nn / 2;
             }
         }
        if(n < 0) ans = (double)(1.0)/(double)(ans); //if power is -ve like 2^-1 == 1/2^n
        return ans; 
    }
}
```
