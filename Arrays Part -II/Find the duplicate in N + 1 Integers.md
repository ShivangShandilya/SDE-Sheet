Problem - [Find the duplicate in N + 1 Integers](https://leetcode.com/problems/find-the-duplicate-number/)

- Given an array of N + 1 size, where each element is between 1 and N. Assuming there is only one duplicate number, your task is to find the duplicate number.

Example 1: 

    Input: arr=[1,3,4,2,2]

    Output: 2

Explanation: Since 2 is the duplicate number the answer will be 2.

Example 2:

    Input: [3,1,3,4,2]

    Output:3

Explanation: Since 3 is the duplicate number the answer will be 3.

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
class Solution {
    public int findDuplicate(int[] arr) {
        int i=0;
        while(i < arr.length){
            if(arr[i]!= i+1){
                int correct = arr[i]-1;
            if(arr[i]!=arr[correct]){
                swap(arr, i, correct);
            }else{
                return arr[i];
            }
            }
            else{
                i++;
            }  
        }
        return -1;
    }
            
    void swap(int arr[],int first,int second){
        int temp = arr[first];
        arr[first]=arr[second];
        arr[second]=temp;
    }
}
```
