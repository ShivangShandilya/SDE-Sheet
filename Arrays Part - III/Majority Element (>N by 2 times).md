Problem - [Majority Element (>N by 2 times)](https://leetcode.com/problems/majority-element/)

-  Given an array of N integers, write a program to return an element that occurs more than N/2 times in the given array. You may consider that such an element always exists in the array.

- Example 1:

      Input Format: N = 3, nums[] = {3,2,3}

      Result: 3

Explanation: When we just count the occurrences of each number and compare with half of the size of the array, you will get 3 for the above solution. 

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public int majorityElement(int[] nums){
        Map<Integer,Integer> counts = countNums(nums);
        
        Map.Entry<Integer,Integer> majorityEntry = null;
        for (Map.Entry<Integer, Integer> entry : counts.entrySet()) {
            if (majorityEntry == null || entry.getValue() > majorityEntry.getValue()) {
                majorityEntry = entry;
            }
        }

        return majorityEntry.getKey();
    }
    
    private Map<Integer,Integer> countNums(int[] nums){ 
        Map<Integer,Integer> counts = new HashMap<Integer,Integer>();
        for(int num: nums){
            if(!counts.containsKey(num)){
                counts.put(num,1);
            }
            else{
                counts.put(num, counts.get(num)+1);
            }
        }
        return counts;
    }
}
```
