**Link**: https://leetcode.com/problems/group-anagrams/description/

Tags: #Leetcode 

Status: #adult

**Description**: 
Given an array of strings `strs`, group the anagrams together. You can return the answer in **any order**.

**Example 1:**

**Input:** strs = ["eat","tea","tan","ate","nat","bat"]

**Output:** [[["bat"],["nat","tan"],["ate","eat","tea"]]]

**Explanation:**

- There is no string in strs that can be rearranged to form `"bat"`.
- The strings `"nat"` and `"tan"` are anagrams as they can be rearranged to form each other.
- The strings `"ate"`, `"eat"`, and `"tea"` are anagrams as they can be rearranged to form each other.

**Example 2:**

**Input:** strs = [""]

**Output:** [[""]]

**Example 3:**

**Input:** strs = ["a"]

**Output:** [["a"]]

**Constraints:**

- `1 <= strs.length <= 104`
- `0 <= strs[i].length <= 100`
- `strs[i]` consists of lowercase English letters.

# Code

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        ans = {}
        for item in strs:
            word = ''.join(sorted(item))
            if word in ans:
                ans[word].append(item)
            else:
                ans[word] = [item]
        return list(ans.values())
```
## Time and Space Complexity

- Time complexity: `O(m * n log n)` → `m` = number of words, `n` = avg word length (sorting each word).
- Space complexity: `O(m * n)` → storing all words plus their sorted keys.
## Explanation
- Create a dictionary `ans` to group words.
    
- Loop through each string in `strs`.
    
- Sort the characters in the string → gives a "signature" that’s identical for all anagrams.
    
- Use that sorted signature as the dictionary key.
    
- If key exists → append the original word to that list.
    
- If not → create a new list with that word.
    
- At the end, return just the grouped lists (`list(ans.values())`).
