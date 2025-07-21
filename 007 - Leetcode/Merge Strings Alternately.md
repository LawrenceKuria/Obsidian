**Link**: https://leetcode.com/problems/merge-strings-alternately/description/

Tags: #Arrays-and-Strings [[Leetcode]]

Status: #child 

**Description**: You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return _the merged string._


# Code
```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        len1, len2 = len(word1), len(word2)
        
        ans = ''
        for i in range(min(len1, len2)):
                ans += word1[i]
                ans += word2[i]
        if len1 > len2:
            ans += word1[len2:]
        else:
            ans += word2[len1:]
        return ans
        

```

## Time and Space Complexity

- Time complexity: `O(n + m)` where `n` is length of word 1 and `m` is length of word 2
- Space complexity: `O(n + m)`
## Explanation

