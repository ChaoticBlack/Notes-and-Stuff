There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return _the index of_ `target` _if it is in_ `nums`_, or_ `-1` _if it is not in_ `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

## Solution
```audio-player
[[Search in Rotated Sorted Array.mp3]]
```

## My Code

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left = 0;
        int right = nums.size()-1;
        return binarySearch(nums,target,left,right);
    }

    int binarySearch(vector<int>& nums, int target, int left, int right)
    {
        if(left>right)
            return -1;
        int mid = (left+right)/2;
        if(nums[mid]==target)
            return mid;
        if(nums[mid]>=nums[left]) //condition 1  //means all the elements greater than left and less than mid are to the left of mid
        {
            if(nums[mid]>target && target>=nums[left])  //target is within this range, so go left
            {
                right=mid-1;
                return binarySearch(nums,target,left,right);
            }
            left=mid+1; // above if failing means target is not in this range so go right
            return binarySearch(nums,target,left,right);

        }
        // if(nums[mid]<=nums[right])   //condition 2
        // commented if is implied as for any rotation of array, either condition 1 or condition 2 is always true
        if(nums[mid]<target && target<=nums[right]) //target is within this range, so go left
        {
            left=mid+1;
            return binarySearch(nums,target,left,right);
        }
        right=mid-1;    //// above if failing means target is not in this range so go left
        return binarySearch(nums,target,left,right);
        

    }
};
```

## Complexity
- Time - O(log n)
- Space - O(1)


## Ideal Code
same as above

## Complexity
- Time - O(log n)
- Space - O(1)


## My Notes
extremely good problem. Makes you think binary search from the ground up. Revise well.

### Tags
#medium #BinarySearch 