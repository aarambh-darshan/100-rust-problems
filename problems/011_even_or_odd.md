# 11. Even or Odd
**Difficulty**: Easy  
**Topics**: Math, Bit Manipulation

## Problem Description

Given an integer `n`, return `"Even"` if the number is even, or `"Odd"` if the number is odd.

## Examples

### Example 1:
```
Input: n = 4
Output: "Even"
```

### Example 2:
```
Input: n = 7
Output: "Odd"
```

### Example 3:
```
Input: n = 0
Output: "Even"
```

## Constraints

- `-10^9 <= n <= 10^9`

## Hints

<details>
<summary>Hint 1</summary>
Use the modulo operator (%) to check if a number is divisible by 2.
</details>

<details>
<summary>Hint 2</summary>
A number is even if n % 2 == 0, otherwise it's odd.
</details>

<details>
<summary>Hint 3</summary>
For a bit manipulation approach: a number is odd if its least significant bit is 1 (n & 1 == 1).
</details>

## Function Signature

```rust
impl Solution {
    pub fn even_or_odd(n: i32) -> String {
        
    }
}
```
