**Link**:

Tags: #Leetcode 

Status: #child

**Description**:


# Code

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        seq = set(nums)
        longest = 0
        for num in seq:
            if num - 1 not in seq:
                next_num = num + 1
                current = 1
                while next_num in seq:
                    current += 1
                    next_num += 1
                longest = max(longest, current)
        
        return longest
```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(n)`
## Explanation
