# 3. Palindrome Number
**Difficulty**: Easy  
**Topics**: Math

## Problem Description

Given an integer `x`, return `true` if `x` is a palindrome, and `false` otherwise.

An integer is a **palindrome** when it reads the same backward as forward.

## Examples

### Example 1:
```
Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.
```

### Example 2:
```
Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

### Example 3:
```
Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

## Constraints

- `-2^31 <= x <= 2^31 - 1`

## Hints

<details>
<summary>Hint 1</summary>
Negative numbers cannot be palindromes. Why?
</details>

<details>
<summary>Hint 2</summary>
You can convert the number to a string and check if it equals its reverse.
</details>

<details>
<summary>Hint 3</summary>
For a math-only solution: reverse only half of the number and compare with the other half.
</details>

## Function Signature

```rust
impl Solution {
    pub fn is_palindrome(x: i32) -> bool {
        
    }
}
```
