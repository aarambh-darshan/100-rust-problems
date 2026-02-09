# 21. Plus One
**Difficulty**: Easy  
**Topics**: Arrays, Math

## Problem Description

You are given a **large integer** represented as an integer array `digits`, where each `digits[i]` is the `i-th` digit of the integer. The digits are ordered from most significant to least significant in left-to-right order.

Increment the large integer by one and return the resulting array of digits.

## Examples

### Example 1:
```
Input: digits = [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123. 123 + 1 = 124.
```

### Example 2:
```
Input: digits = [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321. 4321 + 1 = 4322.
```

### Example 3:
```
Input: digits = [9,9,9]
Output: [1,0,0,0]
Explanation: The array represents the integer 999. 999 + 1 = 1000.
```

## Constraints

- `1 <= digits.len() <= 100`
- `0 <= digits[i] <= 9`
- `digits` does not contain any leading zeros.

## Hints

<details>
<summary>Hint 1</summary>
Start from the rightmost digit (least significant) and work your way left.
</details>

<details>
<summary>Hint 2</summary>
If a digit is less than 9, just increment it and return. Otherwise, set it to 0 and carry over.
</details>

<details>
<summary>Hint 3</summary>
If you've processed all digits and still have a carry, prepend 1 to the result (e.g., 999 → 1000).
</details>

## Function Signature

```rust
impl Solution {
    pub fn plus_one(digits: Vec<i32>) -> Vec<i32> {
        
    }
}
```
