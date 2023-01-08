Problem - [Valid Anagram](https://leetcode.com/problems/valid-anagram/)

- Given two strings s and t, return true if t is an anagram of s, and false otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

- Example 1:

      Input: s = "anagram", t = "nagaram"
      Output: true

- Example 2:

      Input: s = "rat", t = "car"
      Output: false
      
- Solution:

```
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length()!=t.length())
            return false;
        
        int[] alphabet = new int[26];
        for (int i = 0; i < s.length(); i++) alphabet[s.charAt(i) - 'a']++;
        for (int i = 0; i < t.length(); i++) alphabet[t.charAt(i) - 'a']--;
        for (int i : alphabet) if (i != 0) return false;
        return true;
    
    }
}
```
