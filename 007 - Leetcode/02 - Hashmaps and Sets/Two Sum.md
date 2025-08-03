**Link**: https://leetcode.com/problems/two-sum/description/

Tags: #Leetcode 

Status: #adult

**Description**:
Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

**Input:** nums = [2,7,11,15], target = 9
**Output:** [0,1]
**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

**Example 2:**

**Input:** nums = [3,2,4], target = 6
**Output:** [1,2]

**Example 3:**

**Input:** nums = [3,3], target = 6
**Output:** [0,1]

**Constraints:**

- `2 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`
- `-109 <= target <= 109`
- **Only one valid answer exists.**

# Code

```python
class Solution(object):
    def twoSum(self, nums, target):
        seen = {}

        for i, num in enumerate(nums):
            ideal = target - num
            if ideal not in seen:
                seen[num] = i
            else:
                return [i, seen[ideal]]
```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(n)`
## Explanation
- Create `seen` dictionary to remember numbers we’ve visited and their indices.
    
- Loop through `nums` with index `i` and value `num`:
    
    - Compute `ideal` = `target - num` (the number we need).
        
    - If `ideal` is in `seen`, we’ve found the pair → return indices.
        
    - If not, store `num` with its index in `seen`.