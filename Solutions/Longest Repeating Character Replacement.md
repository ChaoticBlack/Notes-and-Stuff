You are given a string `s` and an integer `k`. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most `k` times.

Return _the length of the longest substring containing the same letter you can get after performing the above operations_.

## Solution
```audio-player
[[Longest Repeating Character Replacement.mp3]]
```

## My Code

```cpp
class Solution {
public:
    int characterReplacement(string s, int k) {
        map<char,int> hash;
        int left=0;
        int windowSize = 1;
        int res=0;
        for(int right=0;right<s.size();right++)
        {
            hash[s[right]]++;
            windowSize = right-left+1;
            int mostCommon = 0;
            for(auto i:hash)   //find which char is most common in current window
            {
                if(i.second>mostCommon)
                    mostCommon = i.second;
            }
            while(windowSize-mostCommon>k)   //windowSize-mostCommon = remaining chars in current window
            {
                hash[s[left]]--;
                left++;
                windowSize = right-left+1;
                for(auto i:hash)
	            {
	                if(i.second>mostCommon)
	                    mostCommon = i.second;
	            }
            }
            res= max(res,windowSize);
        }
        return res;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code
Just slightly better written version of above code

## Complexity
- Time - O(n)
- Space - O(n)


## My Notes
fairly intuitve

### Tags
#medium #sliding #HashTable #string 