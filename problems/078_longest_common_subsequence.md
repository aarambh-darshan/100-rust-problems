# 78. Longest Common Subsequence
**Difficulty**: Hard  
**Topics**: String, Dynamic Programming

## Problem Description

Given two strings `text1` and `text2`, return the length of their longest common subsequence. If there is no common subsequence, return `0`.

A **subsequence** of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

A **common subsequence** of two strings is a subsequence that is common to both strings.

## Examples

### Example 1:
```
Input: text1 = "abcde", text2 = "ace"
Output: 3
Explanation: The longest common subsequence is "ace" and its length is 3.
```

### Example 2:
```
Input: text1 = "abc", text2 = "abc"
Output: 3
Explanation: The longest common subsequence is "abc" and its length is 3.
```

### Example 3:
```
Input: text1 = "abc", text2 = "def"
Output: 0
Explanation: There is no such common subsequence, so the result is 0.
```

## Constraints

- `1 <= text1.len(), text2.len() <= 1000`
- `text1` and `text2` consist of only lowercase English characters.

## Hints

<details>
<summary>Hint 1</summary>
Use 2D dynamic programming. dp[i][j] = LCS of text1[0..i] and text2[0..j].
</details>

<details>
<summary>Hint 2</summary>
If text1[i-1] == text2[j-1], dp[i][j] = dp[i-1][j-1] + 1.
</details>

<details>
<summary>Hint 3</summary>
Otherwise, dp[i][j] = max(dp[i-1][j], dp[i][j-1]).
</details>

## Function Signature

```rust
impl Solution {
    pub fn longest_common_subsequence(text1: String, text2: String) -> i32 {
        
    }
}
```
