# 13. Leap Year
**Difficulty**: Easy  
**Topics**: Math, Conditionals

## Problem Description

Given a year, return `true` if it is a leap year, otherwise return `false`.

A year is a leap year if:
- It is divisible by 4 AND
- It is NOT divisible by 100, UNLESS it is also divisible by 400

## Examples

### Example 1:
```
Input: year = 2000
Output: true
Explanation: 2000 is divisible by 400, so it's a leap year.
```

### Example 2:
```
Input: year = 1900
Output: false
Explanation: 1900 is divisible by 100 but not by 400, so it's not a leap year.
```

### Example 3:
```
Input: year = 2024
Output: true
Explanation: 2024 is divisible by 4 but not by 100, so it's a leap year.
```

## Constraints

- `1 <= year <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
A leap year must be divisible by 4.
</details>

<details>
<summary>Hint 2</summary>
If divisible by 100, it must also be divisible by 400 to be a leap year.
</details>

<details>
<summary>Hint 3</summary>
The condition can be written as: (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)
</details>

## Function Signature

```rust
impl Solution {
    pub fn is_leap_year(year: i32) -> bool {
        
    }
}
```
