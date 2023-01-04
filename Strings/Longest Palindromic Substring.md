Problem - [ Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)

- Given a string s, return the longest palindromic substring in s

- Example 1:

      Input: s = "babad"
      Output: "bab"

Explanation: "aba" is also a valid answer.

- Example 2:

      Input: s = "cbbd"
      Output: "bb"
      
- Solution

```
class Solution {
    public String longestPalindrome(String s) {
       if(s == null || s.length() < 1) return "";
        
        int start=0;
        int end=0;
        
        for(int i=0;i<s.length();i++){
            int len1 = expandfromMiddle(s,i,i); // racecar this checks if e is equal to e then left and right
            int len2 = expandfromMiddle(s,i,i+1); // this checks for aabbaa, first b is i and second b is i+1
            int len = Math.max(len1,len2);
            if(len > end-start){
                start = i - ((len-1)/2); // after checking we need start and end to get that substring
                end = i + (len/2);
            }
        }
        return s.substring(start,end+1);
    }
    
    public int expandfromMiddle(String s, int left , int right){ // here we are traversing from middle to both sides
        if(s == null || left > right) return 0;
        
        while(left >= 0 && right < s.length() && s.charAt(left)==s.charAt(right)){
            left--;
            right++;
            }
        return right - left - 1;
    }
    
}
```
