**Link**:

Tags: #Leetcode 

Status: #child

**Description**:

Given an unsorted array of integers `nums`, return _the length of the longest consecutive elements sequence._

You must write an algorithm that runs in `O(n)` time.

**Example 1:**

**Input:** nums = `[100,4,200,1,3,2]`
**Output:** 4
**Explanation:** The longest consecutive elements sequence is `[1, 2, 3, 4]`. Therefore its length is 4.

**Example 2:**

**Input:** nums = `[0,3,7,2,5,8,4,6,0,1]`
**Output:** 9

**Example 3:**

**Input:** nums = `[1,0,1,2]`
**Output:** 3

**Constraints:**

- `0 <= nums.length <= 105`
- `-109 <= nums[i] <= 109`

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

- Convert `nums` to a **set** → fast `O(1)` lookups.
    
- Loop through each number in the set.
    
- If `(num - 1)` is **not** in the set → this is the start of a new sequence.
    
- Count how many consecutive numbers follow it (`num + 1`, `num + 2`, …).
    
- Update `longest` if the current streak is bigger.
    
- Return the longest streak found.