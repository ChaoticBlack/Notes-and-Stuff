Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) with `O(1)` extra memory.

## Solution

```audio-player
[[Reverse String.wav]]
```

## My Code

```cpp
class Solution {
public:
    void reverseString(vector<char>& s) {
        char temp;
        int i=0;
        int j= s.size()-1;
        while(i<=j)
        {
            temp=s[i];
            s[i]=s[j];
            s[j]=temp;
            i++;
            j--;
            
        }
    }
};
```


## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code
mine is ideal
## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
Just be careful with condition for while loop


### Tags
#easy #string #TwoPointers 