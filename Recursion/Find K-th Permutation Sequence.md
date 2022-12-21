Problem - [Find K-th Permutation Sequence](https://leetcode.com/problems/permutation-sequence/)

- Given N and K, where N is the sequence of numbers from 1 to N([1,2,3….. N]) find the Kth permutation sequence.

For N = 3  the 3!  Permutation sequences in order would look like this:-

![image](https://user-images.githubusercontent.com/101946115/208930221-2ff4aa16-4573-47f8-ac39-ae84ba009d8d.png)

- Example 1:

      Input: N = 3, K = 3
 
      Output: “213”

Explanation: The sequence has 3! permutations as illustrated in the figure above. K = 3 corresponds to the third sequence.

- Example 2:

      Input: N = 3, K = 5 

      Result: “312”

Explanation: The sequence has 3! permutations as illustrated in the figure above. K = 5 corresponds to the fifth sequence.

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public String getPermutation(int n, int k) {
        int fact = 1;
        List<Integer> numbers = new ArrayList<>();
        for(int i = 1; i < n; i++){
            fact = fact * i;
            numbers.add(i);
        }
        numbers.add(n);
        String ans = "";
        k = k - 1;
        while(true){
            ans += numbers.get(k / fact);
            numbers.remove(k / fact);
            if(numbers.size() == 0)
                break;
            
            k = k % fact;
            fact = fact / numbers.size();
        }
        return ans;
    }
}
```

