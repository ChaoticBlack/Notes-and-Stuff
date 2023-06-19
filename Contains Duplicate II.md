Given an integer array `nums` and an integer `k`, return `true` _if there are two **distinct indices**_ `i` _and_ `j` _in the array such that_ `nums[i] == nums[j]` _and_ `abs(i - j) <= k`.

## Solution
```audio-player
[[Jump-Game.wav]]
```

## My Code
```cpp
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        set<int> hashTable;
        int left=0;
        int right = 0;
        for (right;right<nums.size();right++)
        {
            if(right-left>k)
            {
                 hashTable.erase(nums[left]);
                 left=left+1;

            }
            if(hashTable.find(nums[right]) != hashTable.end())  //already exists in set
                return true;
            hashTable.insert(nums[right]);
        }
        return false;
    }
};
```

```cpp
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        map<int,int> hashTable;
        for(int i=0;i<nums.size();i++)
        {
            if(hashTable.find(nums[i])!=hashTable.end()) //key already present
            {
                if(abs(hashTable[nums[i]]-i)<=k)
                    return true;
            }
            hashTable[nums[i]] = i;
        }
        return false;
    }
};
```
## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code
set approach of the above is more optimized
## Complexity
- Time - O(n)
- Space - O(n)


## My Notes


### Tags
#easy #sliding #HashTable 