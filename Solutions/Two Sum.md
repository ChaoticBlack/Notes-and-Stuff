Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

## Solution
Just watch neetcode

## My Code

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> dict;
        vector<int> ans;
        for(int i=0;i<nums.size();i++)
        {
            
            int diff= target-nums[i];
            //dict[nums[i]]=diff;
            if(dict.find(diff)!=dict.end())  //diff exists
            {
                ans.push_back(i);
                ans.push_back(dict[diff]);
                return ans;
            }
            dict[nums[i]]=i;
        }
        return ans;
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
When in doubt, Hash Tables <3

### Tags
#easy #array #HashTable 