# 79. Edit Distance
**Difficulty**: Hard  
**Topics**: String, Dynamic Programming

## Problem Description

Given two strings `word1` and `word2`, return the minimum number of operations required to convert `word1` to `word2`.

You have the following three operations permitted on a word:

- Insert a character
- Delete a character
- Replace a character

## Examples

### Example 1:
```
Input: word1 = "horse", word2 = "ros"
Output: 3
Explanation: 
horse -> rorse (replace 'h' with 'r')
rorse -> rose (remove 'r')
rose -> ros (remove 'e')
```

### Example 2:
```
Input: word1 = "intention", word2 = "execution"
Output: 5
Explanation: 
intention -> inention (remove 't')
inention -> enention (replace 'i' with 'e')
enention -> exention (replace 'n' with 'x')
exention -> exection (replace 'n' with 'c')
exection -> execution (insert 'u')
```

## Constraints

- `0 <= word1.len(), word2.len() <= 500`
- `word1` and `word2` consist of lowercase English letters.

## Hints

<details>
<summary>Hint 1</summary>
Use 2D DP. dp[i][j] = min operations to convert word1[0..i] to word2[0..j].
</details>

<details>
<summary>Hint 2</summary>
If characters match, dp[i][j] = dp[i-1][j-1] (no operation needed).
</details>

<details>
<summary>Hint 3</summary>
Otherwise, dp[i][j] = 1 + min(dp[i-1][j-1], dp[i-1][j], dp[i][j-1]) for replace, delete, insert.
</details>

## Function Signature

```rust
impl Solution {
    pub fn min_distance(word1: String, word2: String) -> i32 {
        
    }
}
```
