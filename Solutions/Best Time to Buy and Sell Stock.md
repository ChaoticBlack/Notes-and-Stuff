You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.

## Solution
```audio-player
[[Best Time to Buy and Sell Stock.mp3]]
```

## My Code
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int left=0;     //buy
        int right=0;    //sell
        int maxProfit = 0;
        while(right<prices.size())
        {
            int profit=prices[right]-prices[left];
            maxProfit = max(maxProfit,profit);
            if(prices[right]<prices[left])
                left=right;
            right++;
        }
        return maxProfit;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code
mine is more or less ideal
## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
apparently there is a DP approach also, check it out

### Tags
#easy #sliding 
