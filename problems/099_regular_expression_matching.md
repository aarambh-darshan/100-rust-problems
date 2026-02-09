# 99. Regular Expression Matching
**Difficulty**: Hard  
**Topics**: String, Dynamic Programming, Recursion

## Problem Description

Given an input string `s` and a pattern `p`, implement regular expression matching with support for `'.'` and `'*'` where:

- `'.'` Matches any single character.
- `'*'` Matches zero or more of the preceding element.

The matching should cover the **entire** input string (not partial).

## Examples

### Example 1:
```
Input: s = "aa", p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
```

### Example 2:
```
Input: s = "aa", p = "a*"
Output: true
Explanation: '*' means zero or more of the preceding element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".
```

### Example 3:
```
Input: s = "ab", p = ".*"
Output: true
Explanation: ".*" means "zero or more (*) of any character (.)".
```

## Constraints

- `1 <= s.len() <= 20`
- `1 <= p.len() <= 20`
- `s` contains only lowercase English letters.
- `p` contains only lowercase English letters, `'.'`, and `'*'`.
- It is guaranteed for each appearance of `'*'`, there will be a previous valid character to match.

## Hints

<details>
<summary>Hint 1</summary>
Use 2D dynamic programming. dp[i][j] = true if s[0..i] matches p[0..j].
</details>

<details>
<summary>Hint 2</summary>
Handle '*': it can match zero occurrences (dp[i][j-2]) or one+ occurrences (if current matches, check dp[i-1][j]).
</details>

<details>
<summary>Hint 3</summary>
Base case: dp[0][0] = true. Handle patterns like "a*b*" which can match empty string.
</details>

## Function Signature

```rust
impl Solution {
    pub fn is_match(s: String, p: String) -> bool {
        
    }
}
```
