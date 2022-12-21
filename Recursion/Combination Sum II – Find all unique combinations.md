Problem - [Combination Sum II – Find all unique combinations](https://leetcode.com/problems/combination-sum-ii/)

- Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target. Each number in candidates may only be used once in the combination.

- Example 1:

      Input: candidates = [10,1,2,7,6,1,5], target = 8

      Output: 
      [
      [1,1,6],
      [1,2,5],
      [1,7],
      [2,6]]


Explanation: These are the unique combinations whose sum is equal to target.
 
- Example 2:

      Input: candidates = [2,5,2,1,2], target = 5

      Output: [[1,2,2],[5]]

Explanation: These are the unique combinations whose sum is equal to target.

-Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> ans = new ArrayList<>();
        Arrays.sort(candidates); 
        findCombination(0, candidates, target, ans, new ArrayList<>());
        return ans;
    }
    
    public void findCombination(int ind, int[] arr, int target, List<List<Integer>> ans, List<Integer> ds){
            if(target == 0){
                ans.add(new ArrayList<>(ds));
            return;
        }
        for(int i=ind ;i < arr.length; i++){
            if(i > ind && arr[i] == arr[i-1])continue; // i > ind is for when choosing 2 index if its same we can add but other && condition is whwn choosing starting index it cannot be duplicate.
            if(arr[i] > target)break;
            ds.add(arr[i]);
            findCombination(i + 1, arr, target - arr[i], ans, ds);
            ds.remove(ds.size()-1); // after recursion is finished we backtrack and remove the line where we added the index    
        }
    }
}
```
