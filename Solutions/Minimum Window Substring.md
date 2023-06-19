Given two strings `s` and `t` of lengths `m` and `n` respectively, return _the **minimum window**_ **_substring_** _of_ `s` _such that every character in_ `t` _(**including duplicates**) is included in the window_. If there is no such substring, return _the empty string_ `""`.

The testcases will be generated such that the answer is **unique**.

## Solution
```audio-player
[[Minimum Window Substring.mp3]]
```

## My Code

```cpp
class Solution {
public:
    string minWindow(string s, string t) {
        map<char,int> freqT;
        for(int i=0;i<t.size();i++)
            freqT[t[i]]++;
        int need = freqT.size();
        int left=0;
        int right=0;
        map<char,int> freqS;
        vector<int> res = {0,-2};       //negative so that initial isnot counted
        int have =0;
        for(right=0;right<s.size();right++)
        {
            freqS[s[right]]++;
            if(freqS[s[right]]==freqT[s[right]])    //== makes sures only first occerance is considered and repeated are not
                have++;
            while(have==need)
            {
                int currSize = right - left;
                int resSize = res[1]-res[0];
                if(resSize<0 || currSize<resSize)
                {
                    res[0]=left;
                    res[1]=right;
                }
	                //move left forward
                    freqS[s[left]]--;
                    if(freqS[s[left]]<freqT[s[left]])
                        have--;
                    left++;
            }
        }
        if(res[1]-res[0] +1<0)
            return "";
        string result = "";
        for(int i=res[0];i<=res[1];i++)
            result+=s[i];
        return result;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(s+t)


## Ideal Code
same as above

## Complexity
- Time - O(n)
- Space - O(s+t)


## My Notes
excellent problem, revise well

### Tags
#hard #sliding #HashTable #string 