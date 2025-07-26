**Link**: https://leetcode.com/problems/ransom-note/description/

Tags: #Leetcode 

Status: #child

**Description**:

Given two strings `ransomNote` and `magazine`, return `true` _if_ `ransomNote` _can be constructed by using the letters from_ `magazine` _and_ `false` _otherwise_.

Each letter in `magazine` can only be used once in `ransomNote`.

**Example 1:**

**Input:** ransomNote = "a", magazine = "b"
**Output:** false

**Example 2:**

**Input:** ransomNote = "aa", magazine = "ab"
**Output:** false

**Example 3:**

**Input:** ransomNote = "aa", magazine = "aab"
**Output:** true

**Constraints:**

- `1 <= ransomNote.length, magazine.length <= 105`
- `ransomNote` and `magazine` consist of lowercase English letters.

# Code

```python
from collections import Counter
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        first = Counter(ransomNote)
        second = Counter(magazine)
        for key in first.keys():
            if key in second:
                if first[key] <= second[key]:
                    continue
                else:
                    return False
            else:
                return False
        return True
```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(n)`
## Explanation

- You use `Counter` to count how many times each letter appears in `ransomNote` and `magazine`.
    
- Loop through each unique letter in the ransom note.
    
- If the letter exists in `magazine` **and** there are enough of that letter, continue.
    
- If the letter is **missing** or there aren't **enough copies**, return `False`.
    
- If the loop finishes, it means the ransom note can be built → return `True`.