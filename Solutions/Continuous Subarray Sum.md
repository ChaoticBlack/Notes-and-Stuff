Given an integer array nums and an integer k, return `true` _if_ `nums` _has a **good subarray** or_ `false` _otherwise_.

A **good subarray** is a subarray where:

-   its length is **at least two**, and
-   the sum of the elements of the subarray is a multiple of `k`.

**Note** that:

-   A **subarray** is a contiguous part of the array.
-   An integer `x` is a multiple of `k` if there exists an integer `n` such that `x = n * k`. `0` is **always** a multiple of `k`.

## Solution
```audio-player
[[Jump-Game.wav]]
```

## My Code
```cpp
class Solution {
public:
    bool checkSubarraySum(vector<int>& nums, int k) {
        map<int,int> memo;
        memo[0]=-1;
        int index=0;
        int total=0;
       return dp(nums,k,memo, index, total);
    }
    bool dp(vector<int>& nums, int k, map<int,int>& memo, int index, int total)
    {
        if(index>=nums.size())
        {
            return false;
        }
        total=total+nums[index];
        int remainder = total%k;
        //this below if else structure HAS to be in this form
        if(memo.find(remainder)==memo.end())   //key does not exists in map 
            memo[remainder]=index;
        else if(index-memo[remainder]>1) 
        {
            return true;
        }
        return(dp(nums,k,memo, index+1, total));
    }
};
```
## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code

## Complexity
- Time - O(n)
- Space - O(1)


## My Notes


### Tags