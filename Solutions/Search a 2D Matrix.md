You are given an `m x n` integer matrix `matrix` with the following two properties:

- Each row is sorted in non-decreasing order.
- The first integer of each row is greater than the last integer of the previous row.

Given an integer `target`, return `true` _if_ `target` _is in_ `matrix` _or_ `false` _otherwise_.

You must write a solution in `O(log(m * n))` time complexity.

## Solution
```audio-player
[[Search a 2D Matrix.mp3]]
00:00:11 --- Problem explanation
00:00:43 --- Solution
00:01:57 --- Ideal Solution
```

## My Code

```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        for (int row = 0;row<matrix.size();row++)
        {
            if(matrix[row][matrix[row].size()-1]>=target)
                return(binarySearch(matrix[row],target,0,matrix[row].size()-1));
        }
        return false;
    }
    bool binarySearch(vector<int>& nums,int target,int left, int right)
    {
        if(left>right)
            return false;
        int mid = (left+right)/2;
        if(nums[mid]==target)
            return true;
        if(nums[mid]>target)
        {
            right=mid-1;
            return(binarySearch(nums,target,left,right));
        }
        left=mid+1;
        return(binarySearch(nums,target,left,right));
    }
};
```

## Complexity
- Time - O(m + log n)
- Space - O(1)


## Ideal Code
look up on leetcode when revising

## Complexity
- Time - O(n)
- Space - O(1)


## My Notes


### Tags
#medium #BinarySearch #2DMatrix 