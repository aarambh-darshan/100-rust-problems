# 15. Swap Two Numbers
**Difficulty**: Easy  
**Topics**: Math, Variables

## Problem Description

Given two integers `a` and `b`, swap their values without using a temporary variable.

Return the swapped values as a tuple `(b, a)`.

## Examples

### Example 1:
```
Input: a = 5, b = 10
Output: (10, 5)
```

### Example 2:
```
Input: a = -1, b = 1
Output: (1, -1)
```

### Example 3:
```
Input: a = 0, b = 0
Output: (0, 0)
```

## Constraints

- `-10^9 <= a, b <= 10^9`

## Hints

<details>
<summary>Hint 1</summary>
In Rust, you can simply return (b, a) as a tuple - the swap is implicit!
</details>

<details>
<summary>Hint 2</summary>
For an in-place swap using arithmetic: a = a + b; b = a - b; a = a - b
</details>

<details>
<summary>Hint 3</summary>
For an in-place swap using XOR: a = a ^ b; b = a ^ b; a = a ^ b
</details>

## Function Signature

```rust
impl Solution {
    pub fn swap(a: i32, b: i32) -> (i32, i32) {
        
    }
}
```
