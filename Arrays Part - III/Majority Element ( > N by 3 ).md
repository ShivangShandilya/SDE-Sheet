Problem - [Majority Element ( > N by 3)](https://leetcode.com/problems/majority-element-ii/)

- Given an array of N integers. Find the elements that appear more than N/3 times in the array. If no such element exists, return an empty vector.

- Example 1 :

      Input: N = 5, array[] = {1,2,2,3,2}

      Ouput: 2

Explanation: Here we can see that the Count(1) = 1, Count(2) = 3 and Count(3) = 1.Therefore, the count of 2 is greater than N/3 times. Hence, 2 is the answer.


- Example 2 :

      Input:  N = 6, array[] = {11,33,33,11,33,11}

      Output: 11 33

Explanation: Here we can see that the Count(11) = 3 and Count(33) = 3. Therefore, the count of both 11 and 33 is greater than N/3 times. Hence, 11 and 33 is the answer.

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.


```
public List<Integer> majorityElement(int[] nums) {
	List<Integer> result = new ArrayList<Integer>();
	if (nums.length == 0)
		return result;
	// In the begining, both Trump and Biden don't get a vote
	int firstMajor = Integer.MAX_VALUE, firstSum = 0, secondMajor = Integer.MIN_VALUE, secondSum = 0;
	
	for (int i = 0; i < nums.length; i++) {
		// case 1: I want to vote for Biden or Trump
		if (nums[i] == firstMajor)
			firstSum++;
		else if (nums[i] == secondMajor)
			secondSum++;
		// case 2: I want to run for the president
		else if (firstSum == 0) {
			firstMajor = nums[i];
			firstSum = 1;
		}
		else if (secondSum == 0) {
			secondMajor = nums[i];
			secondSum = 1;
		}
		// case 3: fuck sleepy Joe and crazy Trump, let James be the president
		else {
			firstSum--;
			secondSum--;
		}
	}
	// After election, we need to count the vote again.
	firstSum = 0;
	secondSum = 0;
	for (int i = 0; i < nums.length; i++) {
		if (nums[i] == firstMajor)
			firstSum++;    
		else if (nums[i] == secondMajor)
			secondSum++;
	}
	if (firstSum > nums.length / 3)
		result.add(firstMajor);
	if (secondSum > nums.length / 3)
		result.add(secondMajor);
	return result;
}
```
