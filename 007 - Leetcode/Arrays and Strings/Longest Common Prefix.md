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

- Check if the input list is empty — return `''` if so.
    
- Find the shortest string in the list (common prefix can't be longer than this).
    
- Loop through each character `i` in the shortest string:
    
    - For each word in the list, check if the character at index `i` matches.
        
    - If **any word differs**, return the prefix up to `i`.
        
- If the loop completes with no mismatches, the entire `shortest` string is the prefix.
    
- Return the final result. 
