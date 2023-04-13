Given an array of integers `nums` and an integer `k`, return _the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than_ `k`.

## Solution
```audio-player
[[Subarray Product Less Than K.mp3]]
```

## My Code

```cpp
class Solution {
public:
    int numSubarrayProductLessThanK(vector<int>& nums, int k) {
        if(k<1)
            return 0;
        int count =0;
        int product = 1;
        int i=0;
        int j=0;
        while(j<nums.size())
        {
            product= product* nums[j];
            while(product>=k && i<=j)
            {   
                product = product/nums[i];
                i++;
            }
            count = count + j - i +1;    // this is important in many sliding window questions of this type
            j++;
        }
        return count;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code
Same as above
## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
```cpp
count = count + j - i +1;    // this is important in many sliding window questions of this type
```

Remember this part while solving Sliding window questions where you have to count shit.

### Tags
#array #sliding #medium 