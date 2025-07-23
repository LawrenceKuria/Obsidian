**Link**: https://leetcode.com/problems/merge-intervals/

Tags: #Leetcode 

Status: #child 

**Description**: Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return _an array of the non-overlapping intervals that cover all the intervals in the input_.

**Example 1:**

**Input:** intervals = [[[1,3],[2,6],[8,10],[15,18]]]
**Output:** [[[1,6],[8,10],[15,18]]]
**Explanation:** Since intervals [1,3] and [2,6] overlap, merge them into [1,6].

**Example 2:**

**Input:** intervals = [[[1,4],[4,5]]]
**Output:** [[[1,5]]]
**Explanation:** Intervals [1,4] and [4,5] are considered overlapping.


# Code
```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if not intervals:
            return []

        intervals.sort(key=lambda x: x[0])

        res = []
        current_start, current_end = intervals[0]

        for i in range(1, len(intervals)):
            next_start, next_end = intervals[i]
            if next_start <= current_end:
                current_end = max(current_end, next_end)
            else:
                res.append([current_start, current_end])
                current_start, current_end = next_start, next_end

        res.append([current_start, current_end])

        return res
```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(n)`
## Explanation
