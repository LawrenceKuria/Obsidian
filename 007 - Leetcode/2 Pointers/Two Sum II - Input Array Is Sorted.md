**Link**: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/

Tags: #Leetcode 

Status: #adult 

**Description**:

Given a **1-indexed** array of integers `numbers` that is already **_sorted in non-decreasing order_**, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return _the indices of the two numbers,_ `index1` _and_ `index2`_, **added by one** as an integer array_ `[index1, index2]` _of length 2._

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.

**Example 1:**

**Input:** numbers = `[2,7,11,15]`, target = 9
**Output:** `[1,2]`
**Explanation:** The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return `[1, 2]`.

**Example 2:**

**Input:** numbers = `[2,3,4]`, target = 6
**Output:** `[1,3]`
**Explanation:** The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return `[1, 3]`.

**Example 3:**

**Input:** numbers = `[-1,0]`, target = -1
**Output:** `[1,2]`
**Explanation:** The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return `[1, 2]`.


# Code
## Time and Space Complexity

- Time complexity: `O(n)` — You only scan the array once with two pointers.
- Space complexity: `O(1)` — No extra data structures; just a few variables.
## Explanation
- Start with **two pointers**: `left` at the start, `right` at the end of the array.
    
- While `left < right`:
    
    - Add the two numbers: `numbers[left] + numbers[right]`.
        
    - If the sum is **equal** to the target → return `[left + 1, right + 1]` (since array is 1-indexed).
        
    - If the sum is **less than** the target → move `left` forward (need a bigger sum).
        
    - If the sum is **greater than** the target → move `right` backward (need a smaller sum).
        
- There's always exactly **one** valid solution, so you'll return before the loop ends.