Problem - [Length of Longest Substring without any Repeating Character](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

- Given a String, find the length of longest substring without any repeating character.

- Example 1:

      Input: s = ”abcabcbb”

      Output: 3

Explanation: The answer is abc with length of 3.

- Example 2:

      Input: s = ”bbbbb”

      Output: 1

Explanation: The answer is b with length of 1 units.

<p align = "center">
  <img src ="https://user-images.githubusercontent.com/101946115/207367761-f8b7ce41-6091-4f36-8b30-664decc867b5.png" height = 500 width = 800/ >
  </p>

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashMap<Character,Integer> map = new HashMap<>();
        int left=0,right=0;
        int n = s.length();
        int len=0;
        
        while(right < n){
            if(map.containsKey(s.charAt(right)))
                left = Math.max(map.get(s.charAt(right))+1,left);
            
            map.put(s.charAt(right),right);
            len = Math.max(len,right-left+1);
            right++;
        }
        return len;
    }
}
```
