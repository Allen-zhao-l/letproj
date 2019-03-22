Longest Substring Without Repeating Characters
Given a string, find the length of the longest substring without repeating characters.

##Example 1:

Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 

##Example 2:

Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

##Example 3:

Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
###Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(std::string s) {
        vector<int> vd(256,-1);
        int i,j,start=-1,max=0,len=s.size();
        for (i=0;i!=len;++i)
        {
            if (vd[s[i]]>start) start=vd[s[i]];
            vd[s[i]]=i;
            j=i-start;
            max=max>j?max:j;
        }
        return max;
    }
};

```
