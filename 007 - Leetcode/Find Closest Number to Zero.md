**Link**: https://leetcode.com/problems/find-closest-number-to-zero/description/

Tags:  #Arrays-and-Strings [[Leetcode]]

Status: #adult 

**Description**: Given an integer array `nums` of size `n`, return _the number with the value **closest** to_ `0` _in_ `nums`. If there are multiple answers, return _the number with the **largest** value_.


# Code

```python
class Solution:
    def findClosestNumber(self, nums: List[int]) -> int:
        closest = nums[0]
        for val in nums:
            if abs(val) < abs(closest):
                closest = val
            elif abs(val) == abs(closest):
                closest = max(closest, val)
        return closest

```

- Time complexity: O(n)
- Space complexity: O(1)
## Explanation

- Initialize `closest` to the first number of `nums` because if the array was only 1 element, the closest number would be the first(and only) element.
- Traverse `nums` comparing the absolute value of each element to that of `closest` and if its less than closest than it is closer to 0 and the new closest value.
- In the case where the absolute values are equal, the greater one is favored as per the description.
- Return `closest` at the end.
