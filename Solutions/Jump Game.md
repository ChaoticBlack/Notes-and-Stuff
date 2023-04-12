You are given an integer array `nums`. You are initially positioned at the array's **first index**, and each element in the array represents your maximum jump length at that position.

Return `true` _if you can reach the last index, or_ `false` _otherwise_.

## Solution
```audio-player
[[Jump-Game.wav]]
```


## My Code

```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        //int len = nums.size()-1;
        int index=0;
        vector<bool> reach(nums.size(), false);
        dp(nums,index, reach);
        return(reach.back());
    }

    void dp(vector<int>& nums, int index, vector<bool>& reach)
    {
        // if(reach[index]==true)
        // {
        //     return;
        // }
        if(index + nums[index]>= nums.size()-1)
        {
            reach.back()=true;
            return;
        }
        if(index>nums.size()-1)
            return;
        reach[index]=true;
        for(int i=1;i<=nums[index];i++)
        {
            if(!reach[index+i])
                dp(nums, index+i,reach);
        }
        return;

    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code

## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
look up the greedy approach

### Tags
#medium #dynamic #greedy 