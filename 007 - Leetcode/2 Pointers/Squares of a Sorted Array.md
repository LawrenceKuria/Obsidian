**Link**: https://leetcode.com/problems/squares-of-a-sorted-array/description/

Tags: #Leetcode 

Status: #adult

**Description**:
Given an integer array `nums` sorted in **non-decreasing** order, return _an array of **the squares of each number** sorted in non-decreasing order_.

**Example 1:**

**Input:** nums = [-4,-1,0,3,10]
**Output:** [0,1,9,16,100]
**Explanation:** After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].

**Example 2:**

**Input:** nums = [-7,-3,2,3,11]
**Output:** [4,9,9,49,121]

**Constraints:**

- `1 <= nums.length <= 104`
- `-104 <= nums[i] <= 104`
- `nums` is sorted in **non-decreasing** order.
# Code

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        left = 0
        right = len(nums) - 1
        result = []
        
        while left <= right:
            if abs(nums[left]) < abs(nums[right]):
                result.append(nums[right] ** 2)
                right -= 1
            else:
                result.append(nums[left] ** 2)
                left += 1
        
        result.reverse()
        return result
```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(n)`
## Explanation

- Use **two pointers**: `left` (start) and `right` (end).
    
- Compare absolute values of both ends.
    
- Append the larger square to `result` (since larger abs value → larger square).
    
- Move the pointer that contributed the larger square.
    
- Repeat until all numbers processed.
    
- Reverse `result` at the end (we were adding largest to smallest).