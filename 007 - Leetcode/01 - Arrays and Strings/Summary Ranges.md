**Link**: https://leetcode.com/problems/summary-ranges/description/

Tags: #Leetcode 

Status: #child 

**Description**: You are given a **sorted unique** integer array `nums`.

A **range** `[a,b]` is the set of all integers from `a` to `b` (inclusive).

Return _the **smallest sorted** list of ranges that **cover all the numbers in the array exactly**_. That is, each element of `nums` is covered by exactly one of the ranges, and there is no integer `x` such that `x` is in one of the ranges but not in `nums`.

Each range `[a,b]` in the list should be output as:

- `"a->b"` if `a != b`
- `"a"` if `a == b`

**Example 1:**

**Input:** nums = [0,1,2,4,5,7]
**Output:** ["0->2","4->5","7"]
**Explanation:** The ranges are:
[0,2] --> "0->2"
[4,5] --> "4->5"
[7,7] --> "7"

**Example 2:**

**Input:** nums = [0,2,3,4,6,8,9]
**Output:** ["0","2->4","6","8->9"]
**Explanation:** The ranges are:
[0,0] --> "0"
[2,4] --> "2->4"
[6,6] --> "6"
[8,9] --> "8->9"


# Code
```python
class Solution:
    def summaryRanges(self, nums: List[int]) -> List[str]:
        if not nums:
            return []
        
        start, end = 0, 1
        result = []
        while end < len(nums):
            if nums[end - 1] != nums[end] - 1:
                if end - start == 1:
                    result.append(f'{nums[start]}')
                    start += 1
                else:
                    result.append(f'{nums[start]}->{nums[end - 1]}')
                    start = end
        
            end += 1
        
        if end - start == 1:
            result.append(f'{nums[start]}')
        else:
            result.append(f'{nums[start]}->{nums[end - 1]}')
        
        return result
```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(n)`
## Explanation
- If `nums` is empty, return an empty list.
    
- Use two pointers:
    
    - `start` marks the beginning of a range.
        
    - `end` moves through the array to find where the range ends.
        
- Loop while `end` is within bounds:
    
    - If `nums[end]` is **not consecutive** from `nums[end - 1]`:
        
        - If it's a single number, add just `nums[start]`.
            
        - Otherwise, add the range `"start->end-1"`.
            
        - Move `start` to `end`.
            
    - Always increment `end`.
        
- After the loop, handle the **last remaining range** the same way:
    
    - If it’s a single number, add it.
        
    - If it’s a range, format and add it.
        
- Return the result list of formatted ranges.