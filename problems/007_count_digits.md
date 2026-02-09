# 7. Count Digits
**Difficulty**: Easy  
**Topics**: Math

## Problem Description

Given a positive integer `n`, return the number of digits in `n`.

## Examples

### Example 1:
```
Input: n = 12345
Output: 5
Explanation: The number 12345 has 5 digits.
```

### Example 2:
```
Input: n = 7
Output: 1
Explanation: The number 7 has 1 digit.
```

### Example 3:
```
Input: n = 1000000
Output: 7
Explanation: The number 1000000 has 7 digits.
```

## Constraints

- `1 <= n <= 10^9`

## Hints

<details>
<summary>Hint 1</summary>
You can convert the number to a string and return its length.
</details>

<details>
<summary>Hint 2</summary>
For a math approach, repeatedly divide the number by 10 and count iterations.
</details>

<details>
<summary>Hint 3</summary>
You can also use logarithm: floor(log10(n)) + 1 gives the digit count.
</details>

## Function Signature

```rust
impl Solution {
    pub fn count_digits(n: i32) -> i32 {
        
    }
}
```
