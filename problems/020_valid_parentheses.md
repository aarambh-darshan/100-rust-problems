# 20. Valid Parentheses
**Difficulty**: Easy  
**Topics**: Stack, String

## Problem Description

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

## Examples

### Example 1:
```
Input: s = "()"
Output: true
```

### Example 2:
```
Input: s = "()[]{}"
Output: true
```

### Example 3:
```
Input: s = "(]"
Output: false
```

### Example 4:
```
Input: s = "([])"
Output: true
```

### Example 5:
```
Input: s = "([)]"
Output: false
```

## Constraints

- `1 <= s.len() <= 10^4`
- `s` consists of parentheses only `'()[]{}'`.

## Hints

<details>
<summary>Hint 1</summary>
Use a stack to keep track of opening brackets.
</details>

<details>
<summary>Hint 2</summary>
When you encounter a closing bracket, check if the top of the stack has the matching opening bracket.
</details>

<details>
<summary>Hint 3</summary>
At the end, the stack should be empty for the string to be valid.
</details>

## Function Signature

```rust
impl Solution {
    pub fn is_valid(s: String) -> bool {
        
    }
}
```
