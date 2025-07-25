**Link**: https://leetcode.com/problems/product-of-array-except-self/description/

Tags: #Leetcode 

Status: #adult 

**Description**: Given an integer array `nums`, return _an array_ `answer` _such that_ `answer[i]` _is equal to the product of all the elements of_ `nums` _except_ `nums[i]`.

The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.


# Code
```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        res = [1] * (len(nums))

        prefix = 1
        for i in range(len(nums)):
            res[i] = prefix
            prefix *= nums[i]
        postfix = 1
        for i in range(len(nums) - 1, -1, -1):
            res[i] *= postfix
            postfix *= nums[i]
        return res
```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(n)`
## Explanation
- Start by creating a result array `res` filled with `1`s (same length as `nums`).
    
- Initialize `prefix = 1` — this will hold the product of all numbers _before_ the current index.
    
- **First pass (left to right):**
    
    - For each index `i`, set `res[i] = prefix`.
        
    - Then update `prefix *= nums[i]` to include the current number.
        
- Initialize `postfix = 1` — holds the product of all numbers _after_ the current index.
    
- **Second pass (right to left):**
    
    - Multiply `res[i] *= postfix` to combine prefix and postfix products.
        
    - Then update `postfix *= nums[i]`.
        
- Return `res` — it now holds the product of all elements except `nums[i]`.