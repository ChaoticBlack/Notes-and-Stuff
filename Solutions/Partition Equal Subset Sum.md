Given an integer array `nums`, return `true` _if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or_ `false` _otherwise_.

## Solution
```audio-player
[[Partition Equal Subset Sum.mp3]]
```

## My Code
```cpp
class Solution {
public:
    bool canPartition(vector<int>& nums) {
        int totSum = 0;
        set<int> memo;
        for(int i=0;i<nums.size();i++)
        {
            totSum=totSum+nums[i];        
        }
        if(totSum%2==1)   //can't be divided into 2 parts if sum is odd
            return false;
        int target = totSum/2;
        for(int i=0;i<nums.size();i++)
        {
            set<int> temp;    //you HAVE to take a new set
            for(auto j : memo)
            {
                temp.insert(j+nums[i]);
            }
            temp.insert(nums[i]);
            memo.insert(temp.begin(),temp.end());
            if (memo.find(target) != memo.end())
                return true;
        }
        return false;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code
- Many appraches possible, look them up while revising.

## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
- Always keep your eyes open to subtle obervations

### Tags
#dynamic #medium #array 