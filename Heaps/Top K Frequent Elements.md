Problem - [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)

- Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

- Example 1:

      Input: nums = [1,1,1,2,2,3], k = 2
      Output: [1,2]

- Example 2:

      Input: nums = [1], k = 1 
      Output: [1]
      
- Soluton

```
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        HashMap<Integer,Integer> map = new HashMap<>();
        for(int i : nums){
            map.put(i , map.getOrDefault(i,0) + 1);
        }
        
        PriorityQueue<Integer> minHeap = new PriorityQueue<>((o1,o2) -> map.get(o1) - map.get(o2));
        for(Integer key : map.keySet()){
            minHeap.add(key);
            if(minHeap.size() > k)
                minHeap.poll();
        }
        
        int[] op = new int[k];
        while(!minHeap.isEmpty()){
            op[--k] = minHeap.poll();
        }
        return op;
    }
}
```
 
