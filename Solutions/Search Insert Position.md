Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with `O(log n)` runtime complexity.

## Solution
```audio-player
[[Search Insert Position.mp3]]
00:00:40 --- why returning left
```

## My Code

```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int right = nums.size()-1;
        int left = 0;
       int index = binarySearch(nums,target,right,left);
       return index;
    }

    int binarySearch(vector<int>& nums, int target, int right, int left)
    {
        if(left>right)
        {
            return left;
        }
        int mid = (right + left)/2;
        if(nums[mid]==target)
        {
            return mid;
        }
        if(nums[mid]>target)
        {
            right = mid-1;
            return(binarySearch(nums,target,right,left));
        }
        left = mid+1;
        return(binarySearch(nums,target,right,left));
    }

};
```

## Complexity
- Time - O(log n)
- Space - O(1)


## Ideal Code
mine is ideal

## Complexity
- Time - O(log n)
- Space - O(1)


## My Notes

understand properly why we are returning left when we don't find the target. (explained in audio)

### Tags
#easy #BinarySearch 