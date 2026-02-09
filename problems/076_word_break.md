# 76. Word Break
**Difficulty**: Hard  
**Topics**: Dynamic Programming, Hash Table, String, Trie

## Problem Description

Given a string `s` and a dictionary of strings `word_dict`, return `true` if `s` can be segmented into a space-separated sequence of one or more dictionary words.

**Note** that the same word in the dictionary may be reused multiple times in the segmentation.

## Examples

### Example 1:
```
Input: s = "leetcode", word_dict = ["leet","code"]
Output: true
Explanation: Return true because "leetcode" can be segmented as "leet code".
```

### Example 2:
```
Input: s = "applepenapple", word_dict = ["apple","pen"]
Output: true
Explanation: Return true because "applepenapple" can be segmented as "apple pen apple".
Note that you are allowed to reuse a dictionary word.
```

### Example 3:
```
Input: s = "catsandog", word_dict = ["cats","dog","sand","and","cat"]
Output: false
```

## Constraints

- `1 <= s.len() <= 300`
- `1 <= word_dict.len() <= 1000`
- `1 <= word_dict[i].len() <= 20`
- `s` and `word_dict[i]` consist of only lowercase English letters.
- All the strings of `word_dict` are **unique**.

## Hints

<details>
<summary>Hint 1</summary>
Use dynamic programming. dp[i] = true if s[0..i] can be segmented.
</details>

<details>
<summary>Hint 2</summary>
For each position i, check all words: if dp[i - word.len()] is true and s[i-word.len()..i] == word, then dp[i] = true.
</details>

<details>
<summary>Hint 3</summary>
Use a HashSet for O(1) word lookup.
</details>

## Function Signature

```rust
use std::collections::HashSet;

impl Solution {
    pub fn word_break(s: String, word_dict: Vec<String>) -> bool {
        
    }
}
```
