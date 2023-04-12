You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

## Solution
```audio-player
[[Climbing Stairs.wav]]
```

## My Code
```cpp
class Solution {
public:
    int climbStairs(int n) {
        //fibonacci type problem
        if(n==1)
            return 1;
        if(n==2)
            return 2;
        vector<int> steps(n);
        steps[0]=1; //one step can be climbed in only one way
        steps[1]=2; //two steps canbe climbed in 2 diff ways
        for(int i=2;i<n;i++)
        {
            steps[i]=steps[i-1]+steps[i-2];
        }
        return steps.back();
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code
ideally you just have to store the previous 2 values hence space complexity is O(1)

## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
Identify the type of DP problem it is. Here it is a Fibonacci problem

### Tags
#easy #dynamic 