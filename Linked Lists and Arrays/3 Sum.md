Problem - [3 Sum](https://leetcode.com/problems/3sum/)

- Given an array of N integers, your task is to find unique triplets that add up to give a sum of zero. In short, you need to return an array of all the unique triplets [arr[a], arr[b], arr[c]] such that i!=j, j!=k, k!=i, and their sum is equal to zero.

- Example 1 :

      Input: nums = [-1,0,1,2,-1,-4]

      Output: [[-1,-1,2],[-1,0,1]]

Explanation: Out of all possible unique triplets possible, [-1,-1,2] and [-1,0,1] satisfy the condition of summing up to zero with i!=j!=k

- Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res = new LinkedList();
        
        for(int i=0;i<nums.length-2;i++){    // its -2 so tht it does,nt go out of bound for the 2nd last index
            if(i==0 || (i > 0 && nums[i]!=nums[i-1])){
                int low = i+1;  // for -1 to calculate its triplet we obv wont include it itself so we check next element...
                int high = nums.length-1;
                int sum = 0 - nums[i];
                
                while(low < high){
                    if(nums[low] + nums[high] == sum){
                        res.add(Arrays.asList(nums[i],nums[low],nums[high]));
                    
                    while(low < high && nums[low]==nums[low+1]) low++;
                    while(low < high && nums[high]==nums[high-1]) high--;
                    low++;
                    high--;
                    }
                    else if(nums[low] + nums[high] > sum)
                        high--;
                    
                    else
                        low++;
                }
                
            }
        }
        return res;
    }
}
```
