**Link**: https://leetcode.com/problems/valid-anagram/description/

Tags: #Leetcode 

Status: #adult 

**Description**:

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

**Example 1:**

**Input:** s = "anagram", t = "nagaram"

**Output:** true

**Example 2:**

**Input:** s = "rat", t = "car"

**Output:** false

**Constraints:**

- `1 <= s.length, t.length <= 5 * 104`
- `s` and `t` consist of lowercase English letters.


# Code

```python
class Solution(object):

def isAnagram(self, s, t):

return ''.join(sorted(s)) == ''.join(sorted(t))
```
## Time and Space Complexity

- Time complexity: `O(n log n)`
- Space complexity: `O(1)`
## Explanation

- Self explanatory, albeit inefficient.
- More efficient method: Implement frequency hashmap.