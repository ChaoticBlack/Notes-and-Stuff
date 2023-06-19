Given an integer array `nums`, find the subarray with the largest sum, and return _its sum_.

## Solution

brute force would be to explore all substrings

## My Code

```cpp
class Solution {

public:

int maxSubArray(vector<int>& nums) {
	int tempSum=0;
	int maxSum=nums[0];
	for (int i=0;i<nums.size();i++) // initialize maxSum to biggest element in array
		maxSum=max(maxSum,nums[i]);
	for (int i=0;i<nums.size();i++) //sliding window
	{
		tempSum=tempSum+nums[i];
		if(tempSum>0)
			maxSum=max(maxSum,tempSum);
		else //if by adding an element to tempSum, sum is going negative, then all the elements uptill this element are useless. so move the window ahead by resetting tempSum
			tempSum=0;
	}
	return maxSum;
}

};
```

## Complexity
- Time - O(n)
- Space - O(1)


## Ideal code does not use sliding window so i'm not adding here

will revisit after doing DP


## My Notes:
- Key concept is that if adding an element to the subarray makes the sum negative, then the entire subarray until that point becomes dead weight. So drop it and move forward.
- variable window size problem

## Tags

#medium #DivideandConquer #dynamic 