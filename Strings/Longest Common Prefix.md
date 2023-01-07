Problem - [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)

- Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

- Example 1:

      Input: strs = ["flower","flow","flight"]
      Output: "fl"

- Example 2:

      Input: strs = ["dog","racecar","car"]
      Output: ""

Explanation: There is no common prefix among the input strings.

- Solution

```
class Solution {
    public String longestCommonPrefix(String[] strs) {
         for (int i = 0; i < strs[0].length(); i++) 
        {
            char tmpChar = strs[0].charAt(i); 
            for (int j = 1; j < strs.length; j++) 
            {
                if (strs[j].length() == i || strs[j].charAt(i) != tmpChar) 
                {
                    return strs[0].substring(0, i);
                }
            }
        }
        return strs[0]; 
    }
}
```
