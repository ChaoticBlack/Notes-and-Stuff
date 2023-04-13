The **alternating sum** of a **0-indexed** array is defined as the **sum** of the elements at **even** indices **minus** the **sum** of the elements at **odd** indices.

-   For example, the alternating sum of `[4,2,5,3]` is `(4 + 5) - (2 + 3) = 4`.

Given an array `nums`, return _the **maximum alternating sum** of any subsequence of_ `nums` _(after **reindexing** the elements of the subsequence)_.

A **subsequence** of an array is a new array generated from the original array by deleting some elements (possibly none) without changing the remaining elements' relative order. For example, `[2,7,4]` is a subsequence of `[4,2,3,7,2,1,4]` (the underlined elements), while `[2,4,2]` is not.

## Solution
```audio-player
[[Maximum Alternating Subsequence Sum.mp3]]
```
![[Maximum Alternating Subsequence Sum.jpeg]]

## My Code

```cpp
class Solution {
public:
    long long maxAlternatingSum(vector<int>& nums) {
        int sign = 1;
        vector<vector<int>>  memo(nums.size(),vector<int>(2,-1));
        long long result=0;
        result= dp(nums, 0, sign, result, memo);
        return result;
    }

    long long dp(vector<int>& nums, int index, int sign, long long& result, vector<vector<int>>&  memo)
    {
        if(index==nums.size())
            return result;

        if(memo[index][sign]!=-1)
            return(memo[index][sign]);

        long long total=0;
        if(sign)
        total = nums[index];
        else
        total = -1 * nums[index];
        total = max(total + dp(nums, index+1, !sign, result, memo), dp(nums,index+1,sign,result, memo));
    memo[index][sign]=total;
    return total;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code
`I Do Not Understand this Solution as of writing this`

```cpp
class Solution {
    typedef long long LL;
public:
    long long maxAlternatingSum(vector<int>& A) {
        LL N = A.size(), dp[2] = {};
        for (int i = 0; i < N; ++i) {
            LL next[2] = {};
            next[0] = max(dp[1] + A[i], dp[0]);
            next[1] = max(dp[0] - A[i], dp[1]);
            swap(next, dp);
        }
        return dp[0];
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)


## My Notes


### Tags
#dynamic #medium 