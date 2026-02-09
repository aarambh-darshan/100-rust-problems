# 12. Prime Number Check
**Difficulty**: Easy  
**Topics**: Math

## Problem Description

Given a positive integer `n`, return `true` if `n` is a prime number, otherwise return `false`.

A **prime number** is a natural number greater than 1 that has no positive divisors other than 1 and itself.

## Examples

### Example 1:
```
Input: n = 7
Output: true
Explanation: 7 is only divisible by 1 and 7.
```

### Example 2:
```
Input: n = 4
Output: false
Explanation: 4 is divisible by 1, 2, and 4.
```

### Example 3:
```
Input: n = 1
Output: false
Explanation: 1 is not a prime number.
```

## Constraints

- `1 <= n <= 10^6`

## Hints

<details>
<summary>Hint 1</summary>
Numbers less than or equal to 1 are not prime. 2 is the only even prime number.
</details>

<details>
<summary>Hint 2</summary>
You only need to check divisibility up to the square root of n.
</details>

<details>
<summary>Hint 3</summary>
After checking for 2, you only need to check odd numbers as divisors.
</details>

## Function Signature

```rust
impl Solution {
    pub fn is_prime(n: i32) -> bool {
        
    }
}
```
