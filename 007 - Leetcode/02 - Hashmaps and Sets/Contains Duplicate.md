**Link**: https://leetcode.com/problems/contains-duplicate/description/

Tags: #Leetcode 

Status: #adult

**Description**:

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

**Input:** nums = [1,2,3,1]

**Output:** true

**Explanation:**

The element 1 occurs at the indices 0 and 3.

**Example 2:**

**Input:** nums = [1,2,3,4]

**Output:** false

**Explanation:**

All elements are distinct.

**Example 3:**

**Input:** nums = [1,1,1,3,3,4,3,2,4,2]

**Output:** true

**Constraints:**

- `1 <= nums.length <= 105`
- `-109 <= nums[i] <= 109`

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