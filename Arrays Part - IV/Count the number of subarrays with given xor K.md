Problem - [Count the number of subarrays with given xor K](https://www.interviewbit.com/problems/subarray-with-given-xor/)

- Given an array of integers A and an integer B. Find the total number of subarrays having bitwise XOR of all elements equal to B.

- Examples:

      Input Format:  A = [4, 2, 2, 6, 4] , B = 6
      Result: 4
Explanation: The subarrays having XOR of their elements as 6 are  [4, 2], [4, 2, 2, 6, 4], [2, 2, 6], [6]

     Input Format: A = [5, 6, 7, 8, 9], B = 5
     Result: 2
Explanation:The subarrays having XOR of their elements as 2 are [5] and [5, 6, 7, 8, 9]

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
import java.io.*;
import java.util.*;
public class Solution {
    public int solve(int[] A, int B) {
     HashMap<Integer,Integer> visited = new HashMap<Integer,Integer>(); 
        int c = 0; 
        int cpx = 0;
        int n = A.length;
        for(int i = 0;i<n;i++) {
            cpx = cpx ^ A[i]; 
            if(visited.get(cpx^B) != null) 
                c += visited.get(cpx ^ B); 
            if(cpx == B) {
                c++; 
            }
            if(visited.get(cpx) != null) 
                visited.put(cpx, visited.get(cpx) + 1); 
            else 
                visited.put(cpx, 1); 
        }
        return c; 
    }
}

class TUF {
	public static void main (String[] args) {
		Solution obj = new Solution();
		int[] A = new int[]{4,2,2,6,4};
		int countTotal=obj.solve(A,6);
		System.out.println("The total number of subarrays having a given XOR 
                k is "+countTotal);
	}
}
```
