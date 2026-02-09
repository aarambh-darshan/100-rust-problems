# 2. Reverse String
**Difficulty**: Easy  
**Topics**: Strings, Two Pointers

## Problem Description

Write a function that reverses a string. The input string is given as a vector of characters `s`.

You must do this by modifying the input vector in-place with O(1) extra memory.

## Examples

### Example 1:
```
Input: s = ['h','e','l','l','o']
Output: ['o','l','l','e','h']
```

### Example 2:
```
Input: s = ['H','a','n','n','a','h']
Output: ['h','a','n','n','a','H']
```

## Constraints

- `1 <= s.len() <= 10^5`
- `s[i]` is a printable ASCII character.

## Hints

<details>
<summary>Hint 1</summary>
Think about swapping elements from the beginning and end of the vector.
</details>

<details>
<summary>Hint 2</summary>
Use two pointers - one starting from the beginning and one from the end.
</details>

<details>
<summary>Hint 3</summary>
Swap elements at the two pointers and move them towards the center until they meet.
</details>

## Function Signature

```rust
impl Solution {
    pub fn reverse_string(s: &mut Vec<char>) {
        
    }
}
```
