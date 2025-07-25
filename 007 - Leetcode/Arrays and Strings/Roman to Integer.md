**Link**: https://leetcode.com/problems/roman-to-integer/description/

Tags:  #Arrays-and-Strings #Hashmap [[Leetcode]]

Status: #adult 

**Description**: Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.

**Symbol**       **Value**
I             1
V             5
X             10
L             50
C             100
D             500
M             1000

For example, `2` is written as `II` in Roman numeral, just two ones added together. `12` is written as `XII`, which is simply `X + II`. The number `27` is written as `XXVII`, which is `XX + V + II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

- `I` can be placed before `V` (5) and `X` (10) to make 4 and 9. 
- `X` can be placed before `L` (50) and `C` (100) to make 40 and 90. 
- `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer.


# Code

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        roman = {'I':1, 'V':5, 'X':10, 'L':50, 'C':100, 'D':500, 'M':1000}
        i = 0
        m = len(s)
        total = 0
        while i < m:
            val1 = s[i]
            if i != m - 1:
                val2 = s[i + 1]
            else:
                val2 = 'I'
            if roman[val1] >= roman[val2] or (i + 1 == m):
                total += roman[val1]
                i +=1
            else:
                total += roman[val2] - roman[val1]
                i += 2
        return total
        

```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(1)`
## Explanation
- Create a dictionary `roman` that maps Roman characters to their integer values.
    
- Initialize `i = 0` to iterate through the string, `m = len(s)` as its length, and `total = 0` to store the result.
    
- Use a `while` loop to process each character:
    - Get the current symbol `val1 = s[i]`.
        
    - If `i` is not at the last character, set `val2 = s[i + 1]`; otherwise default `val2 = 'I'` (acts like a safe dummy).
        
    - Compare values:
        - If `val1` is **greater than or equal to** `val2`, or we're at the last character:
            - Add `roman[val1]` to `total` and move one step.
                
        - Else (means it's a subtractive pair like IV or IX):
            - Add `roman[val2] - roman[val1]` to `total` and move two steps.
                
- Return the total.