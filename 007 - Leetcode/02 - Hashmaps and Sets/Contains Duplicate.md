**Link**:

Tags: #Leetcode 

Status: #child

**Description**:


# Code

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        ans = {}
        for val in nums:
            if val in ans:
                return True
            else:
                ans[val] = 1
        return False
```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(n)`
## Explanation

- You create an empty dictionary `ans` to keep track of seen numbers.
    
- Loop through each number in the list `nums`.
    
- If the number is **already in** `ans`, it means it's a duplicate → return `True`.
    
- If not, add the number to `ans` with any value (like `1`).
    
- If the loop finishes with no duplicates found, return `False`.