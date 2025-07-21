**Link**: https://leetcode.com/problems/is-subsequence/description/

Tags: #Arrays-and-Strings #Two-Pointer [[Leetcode]]

Status: #adult 

**Description**: Given two strings `s` and `t`, return `true` _if_ `s` _is a **subsequence** of_ `t`_, or_ `false` _otherwise_.

A **subsequence** of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., `"ace"` is a subsequence of `"abcde"` while `"aec"` is not).


# Code

```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        i, j = 0, 0
        while i < len(s) and j < len(t):
            if s[i] == t[j]:
                i += 1
            j += 1
        return i == len(s)

```
## Time and Space Complexity

- Time complexity: `O(s + t)`
- Space complexity: `O(1)`
## Explanation

- Initialize two pointers(`i` and `j`) with one pointing the first character of string `s` and the other to the first character of string `t`.
- While the character the pointers point to is less than the length of their respective characters, check if the character at `s[i] == t[j]`
- If this is true, then that is a successful start of a subsequence and you can increment to the next character of `s`.
- Constantly increment `j`, as in order to be a subsequence the characters in `s` must appear in the same relative order in `t`.
- By the end of the while loop, `s` is a subsequence of t iff `i == len(s)`, because that implies every character in `s` appears in the same relative order in `t`.