# 29. Best Time to Buy and Sell Stock
**Difficulty**: Easy  
**Topics**: Arrays, Dynamic Programming

## Problem Description

You are given an array `prices` where `prices[i]` is the price of a given stock on the `i-th` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return `0`.

## Examples

### Example 1:
```
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
```

### Example 2:
```
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```

## Constraints

- `1 <= prices.len() <= 10^5`
- `0 <= prices[i] <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
Track the minimum price seen so far as you iterate through the array.
</details>

<details>
<summary>Hint 2</summary>
For each day, calculate the profit if you were to sell on that day (current price - min price so far).
</details>

<details>
<summary>Hint 3</summary>
Keep track of the maximum profit seen. Update min_price and max_profit as you go.
</details>

## Function Signature

```rust
impl Solution {
    pub fn max_profit(prices: Vec<i32>) -> i32 {
        
    }
}
```
