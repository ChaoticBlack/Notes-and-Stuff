You are given a **sorted unique** integer array `nums`.

A **range** `[a,b]` is the set of all integers from `a` to `b` (inclusive).

Return _the **smallest sorted** list of ranges that **cover all the numbers in the array exactly**_. That is, each element of `nums` is covered by exactly one of the ranges, and there is no integer `x` such that `x` is in one of the ranges but not in `nums`.

Each range `[a,b]` in the list should be output as:

- `"a->b"` if `a != b`
- `"a"` if `a == b`

## Solution
```audio-player
[[Summary Ranges.mp3]]
```

## My Code

```cpp
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        if(nums.size()==0)
        {
            vector<string> res={};
            return res;
        }
        if(nums.size()==1)
        {
            vector<string> res= {to_string(nums[0])};
            return res;
        }
        vector<string> res;
        for(int i =0;i<nums.size();i++)
        {
            string s = "";
            s+=to_string(nums[i]);
            int start = i;
            while(i<nums.size()-1 && nums[i+1]==nums[i]+1)
            {
                i++;
            }
            if(i!=start)
            {
                s.push_back('-');
                s.push_back('>');
                s+= to_string(nums[i]);
            }
            
            res.push_back(s);
        }
        return res;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code

## Complexity
- Time - O(n)
- Space - O(n)


## My Notes


### Tags
#easy #array 