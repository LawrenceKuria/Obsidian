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

- We first start by sorting the `intervals` in ascending order by the start value of each interval of each  so we can merge in one pass.
- After sorting, we create a for loop starting from the second element ranging the length of the `intervals` list.
- We initialize the `res` array to store the merged intervals and set `current_start` and `current_end` to the start and end values respectively of the first interval in `intervals`.
- In our for loop we set `next_start` and `next_end` to the start and end values respectively in  the i'th interval in `intervals`.
- We then check if `next_start <= current_end` and if so, we set `current_end` to the max of `current_end` and `next_end` because this means the next interval was a part of the current interval.
- If the condition is not met then the interval is independent and we can just add the current interval to the `res` array then set the current interval to the next interval and continue the loop.
- At the end we append the current start and end values as the loop can finish without appending them and return our final answer, `res`.