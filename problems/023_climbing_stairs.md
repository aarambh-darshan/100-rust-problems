# 23. Climbing Stairs
**Difficulty**: Easy  
**Topics**: Dynamic Programming, Math

## Problem Description

You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

## Examples

### Example 1:
```
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

### Example 2:
```
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

## Constraints

- `1 <= n <= 45`

## Hints

<details>
<summary>Hint 1</summary>
Think about how you can reach step n. You can come from step n-1 (1 step) or step n-2 (2 steps).
</details>

<details>
<summary>Hint 2</summary>
This is a Fibonacci-like problem! ways(n) = ways(n-1) + ways(n-2)
</details>

<details>
<summary>Hint 3</summary>
Use iteration with just two variables to store the previous two values, achieving O(1) space.
</details>

## Function Signature

```rust
impl Solution {
    pub fn climb_stairs(n: i32) -> i32 {
        
    }
}
```
