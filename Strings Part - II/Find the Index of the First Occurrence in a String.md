Problem - [Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/)

- Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

- Example 1:

      Input: haystack = "sadbutsad", needle = "sad"
      Output: 0

Explanation: "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.

- Example 2:

      Input: haystack = "leetcode", needle = "leeto"
      Output: -1

Explanation: "leeto" did not occur in "leetcode", so we return -1.

- Solution:

```
class Solution {
    public int strStr(String haystack, String needle) {
        if(haystack == null || needle == null || needle.length() > haystack.length()) return -1;
        
        int[] parr = kmpPreprocess(needle);
        int i = 0, j = 0;
        while(i < haystack.length() && j < needle.length()) {
            if(haystack.charAt(i) == needle.charAt(j)) {
                i++; j++;
            } else if(j > 0) {
                j = parr[j - 1];
            } else {
                i++;
            }
        }
        return j == needle.length() ? i - j : -1;
    }

    private int[] kmpPreprocess(String pattern) {
        int i = 1, j = 0;
        int[] res = new int[pattern.length()];
        while(i < pattern.length()) {
            if(pattern.charAt(i) == pattern.charAt(j)) {
                res[i] = j+1;
                i++; j++;
            } else if (j > 0) {
                j = res[j-1];
            } else {
                res[i] = 0;
                i++;
            }
        }
        return res;
    }
}
```
