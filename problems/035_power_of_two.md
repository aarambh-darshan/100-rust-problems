# 35. Power of Two
**Difficulty**: Easy  
**Topics**: Math, Bit Manipulation

## Problem Description

Given an integer `n`, return `true` if it is a power of two. Otherwise, return `false`.

An integer `n` is a power of two, if there exists an integer `x` such that `n == 2^x`.

## Examples

### Example 1:
```
Input: n = 1
Output: true
Explanation: 2^0 = 1
```

### Example 2:
```
Input: n = 16
Output: true
Explanation: 2^4 = 16
```

### Example 3:
```
Input: n = 3
Output: false
```

## Constraints

- `-2^31 <= n <= 2^31 - 1`

## Hints

<details>
<summary>Hint 1</summary>
A power of two has exactly one bit set in its binary representation.
</details>

<details>
<summary>Hint 2</summary>
For positive n, if n is a power of two, then n & (n-1) == 0.
</details>

<details>
<summary>Hint 3</summary>
Make sure to handle the case where n <= 0 (not a power of two).
</details>

## Function Signature

```rust
impl Solution {
    pub fn is_power_of_two(n: i32) -> bool {
        
    }
}
```
