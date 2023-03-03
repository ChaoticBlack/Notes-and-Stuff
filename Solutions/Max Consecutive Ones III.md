Given a binary array `nums` and an integer `k`, return _the maximum number of consecutive_ `1`_'s in the array if you can flip at most_ `k` `0`'s.
## Solution
Intution is basically, we want the longest subarray containing maximum 1s and k zeroes. In other words,  Find the longest subarray with at most k zeros.

For each `A[j]`, try to find the longest subarray.  
If `A[i] ~ A[j]` has zeros <= `K`, we continue to increment `j`.  
If `A[i] ~ A[j]` has zeros > `K`, we increment `i` (as well as `j`).

## My Code

```cpp
class Solution {
public:
    int longestOnes(vector<int>& nums, int k) {
        int i=0;
        int j=0;
        for(j=0;j<nums.size();j++)
        {
            if(nums[j]==0)
            {
                k--;
            }
            if(k<0)
            {
                if(nums[i]==0)
                {
                    k++;
                }
                i++;
            }
        }
        return j-i; //i don't undersand why this is giving the max window size
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code

```python
public int longestOnes(int[] A, int K) {
    int left = 0;
    int right = 0;
    int max = 0;
    
    int numZeroes = 0;
    for (right= 0; right<A.length; right++) {

        if (A[right]==0) numZeroes++;
        
        if (numZeroes > K) {
            if (A[left]==0) numZeroes--;
            left ++;
        }
        if (numZeroes <= K) {
            max = Math.max(max, right-left +1 );
        }
    }
    return max;
}
```


## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
- The intution was the difficult part. code is straightforward.