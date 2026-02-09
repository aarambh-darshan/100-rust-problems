# 22. Sqrt(x)
**Difficulty**: Easy  
**Topics**: Math, Binary Search

## Problem Description

Given a non-negative integer `x`, return the **square root of x** rounded down to the nearest integer. The returned integer should be **non-negative** as well.

You **must not use** any built-in exponent function or operator.

## Examples

### Example 1:
```
Input: x = 4
Output: 2
Explanation: The square root of 4 is 2.
```

### Example 2:
```
Input: x = 8
Output: 2
Explanation: The square root of 8 is 2.82842..., and since we round it down to the nearest integer, 2 is returned.
```

## Constraints

- `0 <= x <= 2^31 - 1`

## Hints

<details>
<summary>Hint 1</summary>
Use binary search to find the largest integer whose square is less than or equal to x.
</details>

<details>
<summary>Hint 2</summary>
Search in the range [0, x]. For each mid value, check if mid * mid <= x.
</details>

<details>
<summary>Hint 3</summary>
Be careful of integer overflow when computing mid * mid. Use i64 for the multiplication.
</details>

## Function Signature

```rust
impl Solution {
    pub fn my_sqrt(x: i32) -> i32 {
        
    }
}
```
