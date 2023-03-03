Given a string `s`, find the length of the **longest** **substring** without repeating characters.


## Solution

brute force would be to explore all substrings


## My Code

```cpp
class Solution {

public:

int lengthOfLongestSubstring(string s) {
	int len=0;
	map<char,vector<int>> count;
	if(s.size()==0 || s.size()==1) //base case
		return s.size();
		for(int i=0;i<s.size();i++)//start sliding window
	{
		if(count.find(s[i])!=count.end()) //duplicate found
		{
			int index=count[s[i]][1]; //index is the first occurance of the element found
			map<char, vector<int>>::iterator it = count.begin();
			while (it != count.end()) //slide the window ahead by deleteing all the elements that occured before the duplicate
			{
				if(it->second[1]<index)
				{
					it=count.erase(it);
				}
				else
					++it;
			}
		}
		count[s[i]]=vector<int>({1,i});
		int temp= count.size();
		len= max(len,temp);
	}
	return len;
	}
};
```


## Complexity
- Time - O(s)
- Space - O(s)

## Ideal code

``` cpp
class Solution {
public:
	int lengthOfLongestSubstring(string s) 
	{
		unordered_set<char> set;
    
		int i = 0, j = 0, n = s.size(), ans = 0;
    
		while( i<n && j<n)
		{
			if(set.find(s[j]) == set.end()) //If the character does not in the set
			{
				set.insert(s[j++]); //Insert the character in set and update the j counter
				ans = max(ans, j-i); //Check if the new distance is longer than the current answer
			}
			else
			{
				set.erase(s[i++]); 
				/*If character does exist in the set, ie. it is a repeated character, 
				we update the left side counter i, and continue with the checking for substring. */
			}
		}
    
		return ans;
	}
};
```


## My Notes
- instead of using map and vector in map using a set would have been better.
- the key concept was, after finding the duplicate, move the window ahead by as many elements as it takes to find the first occerance of this duplicate. now the window has fresh non repeating string. While doing this, update the map by removing deleted elements.
- variable window size problem
