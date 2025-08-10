**Link**: https://leetcode.com/problems/majority-element/description/

Tags: #Leetcode 

Status: #adult 

**Description**:
Given an array `nums` of size `n`, return _the majority element_.

The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

**Example 1:**

**Input:** nums = [3,2,3]
**Output:** 3

**Example 2:**

**Input:** nums = [2,2,1,1,1,2,2]
**Output:** 2

**Constraints:**

- `n == nums.length`
- `1 <= n <= 5 * 104`
- `-109 <= nums[i] <= 109`
# Code
```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        count = 0
        result = 0
        for item in nums:
            if count == 0:
                result = item
                count = 1
            elif result == item:
                count += 1
            else:
                count -= 1
        return result
```

## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(1)`
## Explanation
- Use **Boyer–Moore Voting Algorithm**.
    
- `count` tracks balance; `result` stores the current candidate.
    
- If `count` is zero → pick the current number as new candidate.
    
- If current number matches candidate → increment `count`.
    
- Else → decrement `count`.
    
- By the end, candidate in `result` is guaranteed to be the majority element.