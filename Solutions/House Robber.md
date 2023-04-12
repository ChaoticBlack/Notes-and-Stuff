You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given an integer array `nums` representing the amount of money of each house, return _the maximum amount of money you can rob tonight **without alerting the police**_.

## Solution

```audio-player
[[House Robber.wav]]
```

## My Code

```cpp
class Solution {
public:
    int rob(vector<int>& nums) {
        int robbed=0;
        vector<int> memo(nums.size(),-1);   //memo[i]=max robbery possible till the index i
        robbed=max(dp(0,nums,robbed,memo), dp(1,nums,robbed,memo));
        return robbed;
    }
    int dp(int index, vector<int>& nums, int robbed, vector<int>& memo)
    {
        if(index>=nums.size())
        {
            return robbed;
        }
        if(memo[index]!=-1) //means recursion call for that index has already been called
        {
            return memo[index];
        }

        robbed =  max(robbed +nums[index]+dp(index+2,nums,robbed,memo), dp(index+1,nums,robbed,memo));
        memo[index]=robbed;
        return robbed;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code

## Complexity
- Time - O(n)
- Space - O(1) check this once


## My Notes
standard problems

### Tags
#dynamic #dynamic 