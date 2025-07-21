**Link**: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/

Tags: #Arrays-and-Strings #Two-Pointer [[Leetcode]]

Status: #adult 

**Description**: You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.


# Code

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        i, j = 0, 1
        m = len(prices)
        max_profit = 0
        while j < m:
            buy = prices[i]
            sell = prices[j]
            if buy >= sell:
                i = j
            else:
                current_profit = sell - buy
                max_profit = max(current_profit, max_profit)
            j += 1
        return max_profit
         

```
## Time and Space Complexity

- Time complexity: `O(n)`
- Space complexity: `O(1)`
## Explanation

- Start with a left pointer pointing to the buy date(array index) and a right pointer pointing to the sell date
- If the buy price is greater than or equal to the sell price then you would lose money so we set the buy date to the sell date and increment the sell date by 1
- If the buy price is less than the sell price, then we calculate current profit and update max profit(initialized to 0) as well and increment sell date by 1.
- Return max profit at the end.