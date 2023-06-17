Given an array of integers `nums` sorted in non-decreasing order, find the starting and ending position of a given `target` value.

If `target` is not found in the array, return `[-1, -1]`.

You must write an algorithm with `O(log n)` runtime complexity.

## Solution
```audio-player
[[ind First and Last Position of Element in Sorted Array.mp3]]
```

## My Code

```cpp
    class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        int right = nums.size()-1;
        int left = 0;
        return(binarySearch(nums,target,right,left));
    }
    vector<int> binarySearch(vector<int>& nums, int target, int right, int left)
    {
        vector<int> res = {-1,-1};
        if(left>right)
        {
            // vector<int> res = {-1,1};
            return res;
        }
        int mid = (left+right)/2;
        if(nums[mid]==target)
        {
            int i=mid;
            while(i>=0 && nums[i]==target)
            {
                i--;
            }
            res[0]=i+1;
            int j=mid;
            while(j<nums.size() and nums[j]==target)
            {
                j++;
            }
            res[1]=j-1;
            return res;
        }
        if (nums[mid]>target)
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
- Time - O(log n)  (worst case O(n))
- Space - O(1)


## Ideal Code
```cpp
vector<int> searchRange(int A[], int n, int target) {
    int i = 0, j = n - 1;
    vector<int> ret(2, -1);
    // Search for the left one
    while (i < j)
    {
        int mid = (i + j) /2;
        if (A[mid] < target) i = mid + 1;
        else j = mid;
    }
    if (A[i]!=target) return ret;
    else ret[0] = i;
    
    // Search for the right one
    j = n-1;  // We don't have to set i to 0 the second time.
    while (i < j)
    {
        int mid = (i + j) /2 + 1;   // Make mid biased to the right
        if (A[mid] > target) j = mid - 1;  
        else i = mid;               // So that this won't make the search range stuck.
    }
    ret[1] = j;
    return ret; 
}
```

## Complexity
- Time - O(log n)
- Space - O(1)


## My Notes
have a look at the ideal solution

### Tags
#medium #BinarySearch 