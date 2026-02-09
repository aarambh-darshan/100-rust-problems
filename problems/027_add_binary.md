# 27. Add Binary
**Difficulty**: Easy  
**Topics**: Math, String, Bit Manipulation

## Problem Description

Given two binary strings `a` and `b`, return their sum as a binary string.

## Examples

### Example 1:
```
Input: a = "11", b = "1"
Output: "100"
```

### Example 2:
```
Input: a = "1010", b = "1011"
Output: "10101"
```

## Constraints

- `1 <= a.len(), b.len() <= 10^4`
- `a` and `b` consist only of `'0'` or `'1'` characters.
- Each string does not contain leading zeros except for the zero itself.

## Hints

<details>
<summary>Hint 1</summary>
Process the strings from right to left (least significant bit first).
</details>

<details>
<summary>Hint 2</summary>
Keep track of a carry. For each position: sum = a_bit + b_bit + carry.
</details>

<details>
<summary>Hint 3</summary>
The result bit is sum % 2, and the new carry is sum / 2. Don't forget to reverse the result at the end.
</details>

## Function Signature

```rust
impl Solution {
    pub fn add_binary(a: String, b: String) -> String {
        
    }
}
```
