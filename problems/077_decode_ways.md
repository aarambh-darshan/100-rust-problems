# 77. Decode Ways
**Difficulty**: Hard  
**Topics**: String, Dynamic Programming

## Problem Description

A message containing letters from `A-Z` can be encoded into numbers using the following mapping:

```
'A' -> "1"
'B' -> "2"
...
'Z' -> "26"
```

To decode an encoded message, all the digits must be grouped then mapped back into letters using the reverse of the mapping above (there may be multiple ways).

Given a string `s` containing only digits, return the number of ways to decode it.

## Examples

### Example 1:
```
Input: s = "12"
Output: 2
Explanation: "12" could be decoded as "AB" (1 2) or "L" (12).
```

### Example 2:
```
Input: s = "226"
Output: 3
Explanation: "226" could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).
```

### Example 3:
```
Input: s = "06"
Output: 0
Explanation: "06" cannot be mapped to "F" because of the leading zero.
```

## Constraints

- `1 <= s.len() <= 100`
- `s` contains only digits and may contain leading zero(s).

## Hints

<details>
<summary>Hint 1</summary>
dp[i] = number of ways to decode s[0..i].
</details>

<details>
<summary>Hint 2</summary>
At each position, you can take 1 or 2 digits. Check if they form valid codes (1-26, no leading zeros).
</details>

<details>
<summary>Hint 3</summary>
Handle edge cases: '0' alone is invalid, but "10" and "20" are valid 2-digit codes.
</details>

## Function Signature

```rust
impl Solution {
    pub fn num_decodings(s: String) -> i32 {
        
    }
}
```
