Suppose an array of length `n` sorted in ascending order is **rotated** between `1` and `n` times. For example, the array `nums = [0,1,2,4,5,6,7]` might become:

- `[4,5,6,7,0,1,2]` if it was rotated `4` times.
- `[0,1,2,4,5,6,7]` if it was rotated `7` times.

Notice that **rotating** an array `[a[0], a[1], a[2], ..., a[n-1]]` 1 time results in the array `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]`.

Given the sorted rotated array `nums` of **unique** elements, return _the minimum element of this array_.

You must write an algorithm that runs in `O(log n) time.`

## Solution
```audio-player
[[Find Minimum in Rotated Sorted Array.mp3]]
```

## My Code

```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int left = 0;
        int right = nums.size()-1;
        int min = 5001;  //constraints
        return(binarySearch(nums,left,right, min));
    }
    int binarySearch(vector<int>& nums,int left, int right, int mini)
    {
        if(left>right)
            return mini;
        if (nums[left]<nums[right])  //in case array is sorted the left most element will be the smallest element
            return min(mini,nums[left]);   
        int mid = (left+right)/2;
        if(nums[mid]<mini)
            mini = nums[mid];
        if(nums[mid]>=nums[left])
        {
            //go right
            left = mid +1;
            return(binarySearch(nums,left,right, mini));
        }
        //go left
        right = mid-1;
        return(binarySearch(nums,left,right, mini));
    }
};
```

## Complexity
- Time - O(log n)
- Space - O(1)


## Ideal Code
same as above
## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
Its a good question, slightly twisted application of binary search. If my explanation was not clear, watch neetcode.

### Tags
#medium #BinarySearch 