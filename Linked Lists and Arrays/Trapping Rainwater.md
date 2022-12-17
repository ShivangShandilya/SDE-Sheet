Problem - [Trapping Rainwater](https://leetcode.com/problems/trapping-rain-water/)

-  Given an array of non-negative integers representation elevation of ground. Your task is to find the water that can be trapped after rain.

- Example 1 :

      Input: height= [0,1,0,2,1,0,1,3,2,1,2,1]
 
      Output: 6

Explanation: As seen from the diagram 1+1+2+1+1=6 unit of water can be trapped

![image](https://user-images.githubusercontent.com/101946115/208231491-948cfcbb-ad67-4ceb-99b4-301de3ddcdb7.png)

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public int trap(int[] height) {
        int n = height.length;
        int res = 0;
        int left = 0;
        int right = n - 1;
        int maxLeft = 0, maxRight = 0;
        
        while(left < right){
            if(height[left] <= height[right]){
                if(height[left] > maxLeft){
                    maxLeft = height[left];
                }
                else
                    res += maxLeft - height[left];
                
                left++;
            }
            else{
                if(height[right] > maxRight)
                    maxRight = height[right];
                
                else
                    res += maxRight - height[right];
                
                right--;
            }
        }
        return res;
    }
}
```
