You are given a **0-indexed** array of **distinct** integers `nums`.

There is an element in `nums` that has the **lowest** value and an element that has the **highest** value. We call them the **minimum** and **maximum** respectively. Your goal is to remove **both** these elements from the array.

A **deletion** is defined as either removing an element from the **front** of the array or removing an element from the **back** of the array.

Return _the **minimum** number of deletions it would take to remove **both** the minimum and maximum element from the array._

## Solution

```audio-player
[[Removing Minimum and Maximum From Array.wav]]
00:00:00 --- Problem Explanation
00:00:39 --- My Solution
00:03:29 --- Optimal Solution
```

![[Removing Minimum and Maximum From Array.jpeg]]

## My Code
```cpp
class Solution {
public:
    int minimumDeletions(vector<int>& nums) {
        int maxIndex=0;
        int minIndex=0;
        int maxNo= nums[0];
        int minNo=nums[0];
        int deletions =0;
        //find max and min elements and their indices
        for(int i=1;i<nums.size();i++)
        {
            if(nums[i]>maxNo)
            {
                maxNo=nums[i];
                maxIndex=i;
            }
            if(nums[i]<minNo)
            {
                minNo=nums[i];
                minIndex=i;
            }
        }
        int right = nums.size()-1;
        int left =0;
        int mid = (right+left)/2;
        int minDiff= abs(mid-minIndex);
        int maxDiff= abs(mid-maxIndex);
        if(maxDiff>=minDiff)
        {
            //delete max element first
            if(maxIndex<=mid)
            {
                //element is in the left part of array
                deletions=deletions+maxIndex+1;
                left=maxIndex+1;
                mid=(left+right)/2;
            }
            else
            {
                //element is in the right part of array
                deletions= deletions +right - maxIndex +1;
                right = maxIndex-1;
                mid=(left+right)/2;
            }
            
            //delete min element now
            //we have new left,right,mid
            if(minIndex<=mid)   //minIndex to left of mid
            {
                deletions=deletions+minIndex+1-left;
                //all done
            }
            else    //minIndex to right of mid
            {
                deletions= deletions +right - minIndex +1;
                //all done
            }
        }
        else        //minDiff>maxDiff
        {
            //delete min element first
            if(minIndex<=mid)
            {
                //element in to the left part of array
                deletions=deletions+minIndex+1;
                left=minIndex+1;
                mid=(left+right)/2;
            }
            else    //element is in the right
            {
                deletions=deletions+right-minIndex+1;
                right=minIndex -1;
                mid=(left+right)/2;
            }
            //delete max element now
            if(maxIndex<=mid)
            {
                deletions=deletions+maxIndex+1-left;
            }
            else
            {
                deletions=deletions+right-maxIndex+1;
            }
        }
        return deletions;
    }
};
```
## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code

```cpp
class Solution {
public:
    int minimumDeletions(vector<int>& nums) {
        int a=0;
        int b=0;
        for(int i=1;i<nums.size();i++)
        {
            if(nums[a]<nums[i])
                a=i;
            if(nums[b]>nums[i])
                b=i;
        }
        if (a > b) swap(a, b);
        int N= nums.size();
        return min({ a + 1 + N - b, b + 1, N - a });
    }
};

```

## Complexity
- Time - O(n)
- Space - O(1)


## My Notes


### Tags
#medium #array #greedy 