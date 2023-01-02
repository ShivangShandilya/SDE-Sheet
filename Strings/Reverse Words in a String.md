Problem - [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)

- Given a string s, reverse the words of the string.

- Example 1:

      Input: s=”this is an amazing program”
      Output: “program amazing an is this”

- Example 2:

      Input: s=”This is decent”
      Output: “decent is This”

Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public String reverseWords(String s) {
        
        int i = s.length() - 1;
        
        String ans = "";
        while(i >= 0){
            while(i >= 0 && s.charAt(i) == ' ') i--;// to remove any spaces ahead of string like blue_____    
            
            int j = i;
            if(i < 0) break;
            
            while(i >= 0 && s.charAt(i) != ' ') i--;
            if(ans.isEmpty()){
                ans = ans.concat(s.substring(i + 1, j + 1));
            }
            else{
                ans = ans.concat(" " + s.substring(i + 1, j + 1));
            }
        }
        return ans;
    }
}
```
