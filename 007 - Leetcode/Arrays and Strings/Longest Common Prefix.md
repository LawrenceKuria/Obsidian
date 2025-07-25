**Link**: https://leetcode.com/problems/longest-common-prefix/description/

Tags: #Leetcode #Arrays-and-Strings 

Status: #child 

**Description**: Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`


# Code
```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        if not strs:
            return ''
        
        shortest = min(strs, key=len)
        
        for i in range(len(shortest)):
            for word in strs:
                if word[i] != shortest[i]:
                    return shortest[:i]
        return shortest           
```

      
## Time and Space Complexity

- Time complexity: `O(n * m)`
- Space complexity: `O(1)`
## Explanation

- 
