**Link**:

Tags: #Leetcode 

Status: #child

**Description**: https://leetcode.com/problems/jewels-and-stones/description/

You're given strings `jewels` representing the types of stones that are jewels, and `stones` representing the stones you have. Each character in `stones` is a type of stone you have. You want to know how many of the stones you have are also jewels.

Letters are case sensitive, so `"a"` is considered a different type of stone from `"A"`.

**Example 1:**

**Input:** jewels = "aA", stones = "aAAbbbb"
**Output:** 3

**Example 2:**

**Input:** jewels = "z", stones = "ZZ"
**Output:** 0

**Constraints:**

- `1 <= jewels.length, stones.length <= 50`
- `jewels` and `stones` consist of only English letters.
- All the characters of `jewels` are **unique**.

# Code

```python
from collections import defaultdict
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        total = defaultdict(int)
        summ = 0
        for letter in stones:
            if letter in total:
                total[letter] += 1
            else:
                total[letter] = 1
        for i in jewels:
                summ += total[i]
        return summ
```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(n)`
## Explanation
- Use a `defaultdict` to count how many times each stone appears.
    
- Loop through each letter in `stones`:
    
    - Increment its count in the `total` map.
        
- Initialize `summ = 0` to store how many jewels you have.
    
- Loop through each jewel in `jewels`:
    
    - Add its count from `total` to `summ`.
        
- Return the final count `summ` — the total number of jewels in your stones.