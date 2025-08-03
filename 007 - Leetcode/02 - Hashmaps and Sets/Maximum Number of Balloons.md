**Link**: https://leetcode.com/problems/maximum-number-of-balloons/description/

Tags: #Leetcode 

Status: #child

**Description**:
Given a string `text`, you want to use the characters of `text` to form as many instances of the word **"balloon"** as possible.

You can use each character in `text` **at most once**. Return the maximum number of instances that can be formed.

**Example 1:**

**![](https://assets.leetcode.com/uploads/2019/09/05/1536_ex1_upd.JPG)**

**Input:** text = "nlaebolko"
**Output:** 1

**Example 2:**

**![](https://assets.leetcode.com/uploads/2019/09/05/1536_ex2_upd.JPG)**

**Input:** text = "loonbalxballpoon"
**Output:** 2

**Example 3:**

**Input:** text = "leetcode"
**Output:** 0

**Constraints:**

- `1 <= text.length <= 104`
- `text` consists of lower case English letters only.

# Code

```python
class Solution:
    def maxNumberOfBalloons(self, text: str) -> int:
        mp = {'b': 0, 'a': 0, 'l': 0, 'o': 0, 'n': 0}
        for letter in text:
            if letter in mp:
                mp[letter] += 1
        
        return min(mp["b"], mp["a"], mp["l"]//2, mp["o"]//2, mp["n"])
```
## Time and Space Complexity

- Time complexity:
- Space complexity:
## Explanation

