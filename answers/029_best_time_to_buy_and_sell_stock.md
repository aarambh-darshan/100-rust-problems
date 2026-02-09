# Solution: Best Time to Buy and Sell Stock

## Complete Runnable Code

```rust
fn max_profit(prices: Vec<i32>) -> i32 {
    if prices.is_empty() {
        return 0;
    }
    
    let mut min_price = prices[0];
    let mut max_profit = 0;
    
    for &price in &prices[1..] {
        // Update max profit if we sell today
        max_profit = max_profit.max(price - min_price);
        // Update minimum price seen so far
        min_price = min_price.min(price);
    }
    
    max_profit
}

fn main() {
    // Test cases
    let test_cases = vec![
        vec![7, 1, 5, 3, 6, 4],
        vec![7, 6, 4, 3, 1],
        vec![1, 2],
        vec![2, 1, 2, 1, 0, 1, 2],
        vec![3, 3, 3],
    ];
    
    for prices in test_cases {
        let profit = max_profit(prices.clone());
        println!("Prices: {:?}", prices);
        println!("Max Profit: ${}\n", profit);
    }
}
```

**Output:**
```
Prices: [7, 1, 5, 3, 6, 4]
Max Profit: $5

Prices: [7, 6, 4, 3, 1]
Max Profit: $0

Prices: [1, 2]
Max Profit: $1

Prices: [2, 1, 2, 1, 0, 1, 2]
Max Profit: $2

Prices: [3, 3, 3]
Max Profit: $0
```

## How It Works

### The Key Insight

For maximum profit, we need to find the minimum price (to buy) BEFORE the maximum price (to sell).

As we scan left to right:
1. Track the minimum price seen so far
2. At each price, calculate potential profit (current - min)
3. Track the maximum profit

### Step-by-Step for [7, 1, 5, 3, 6, 4]

```
Day 0: price=7
  min_price = 7
  profit = 0 (can't sell yet)

Day 1: price=1
  min_price = min(7, 1) = 1
  profit = max(0, 1-7) = 0

Day 2: price=5
  profit = max(0, 5-1) = 4 ← new max!
  min_price = min(1, 5) = 1

Day 3: price=3
  profit = max(4, 3-1) = 4
  min_price = 1

Day 4: price=6
  profit = max(4, 6-1) = 5 ← new max!
  min_price = 1

Day 5: price=4
  profit = max(5, 4-1) = 5
  min_price = 1

Final: Max Profit = $5 (buy at $1, sell at $6)
```

### Visual Representation

```
Prices: [7, 1, 5, 3, 6, 4]

    7 |█
    6 |        █
    5 |    █
    4 |            █
    3 |      █
    2 |
    1 |  █ ← Buy here
      +-----------------
       0  1  2  3  4  5  (day)

Best trade: Buy day 1 ($1) → Sell day 4 ($6) = $5 profit
```

### Why This Works

We're essentially asking: "What's the best profit if I sell TODAY?"

- To maximize profit selling today, I should have bought at the lowest price before today
- We track `min_price` as "best buying opportunity so far"
- We try selling at every price and keep the best

### Decreasing Prices Case

```
[7, 6, 4, 3, 1]

Every day's price is lower than before.
No matter when you buy, you'll sell at a loss.
Best strategy: Don't trade → Profit = 0
```

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass through prices
- **Space Complexity**: O(1) - Only two variables
