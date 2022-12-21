Problem - [Combination Sum – 1](https://leetcode.com/problems/combination-sum/)

- Given an array of distinct integers and a target, you have to return the list of all unique combinations where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from the given array an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

It is guaranteed that the number of unique combinations that sum up to target is less than 150 combinations for the given input.


- Example 1:

      Input: array = [2,3,6,7], target = 7

      Output: [[2,2,3],[7]]

Explanation: 2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
             7 is a candidate, and 7 = 7.
             These are the only two combinations.


- Example 2:

      Input: array = [2], target = 1

      Output: []

Explaination: No combination is possible.

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> ans = new ArrayList<>();
        findCombination(0, candidates, target, ans, new ArrayList<>());
        return ans;
    }
    
    public void findCombination(int ind, int[] arr, int target, List<List<Integer>> ans, List<Integer> ds){
        if(ind == arr.length){
            if(target == 0)
                ans.add(new ArrayList<>(ds));
            return;
        }
        if(arr[ind] <= target){
            ds.add(arr[ind]);
            findCombination(ind, arr, target - arr[ind], ans, ds);
            ds.remove(ds.size()-1); // after recursion is finished we backtrack and remove the line where we added the index    
        }
            findCombination(ind + 1, arr, target, ans, ds);

    }
}
```
