# 31. Valid Anagram
**Difficulty**: Easy  
**Topics**: Strings, HashMap, Sorting

## Problem Description

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Examples

### Example 1:
```
Input: s = "anagram", t = "nagaram"
Output: true
```

### Example 2:
```
Input: s = "rat", t = "car"
Output: false
```

## Constraints

- `1 <= s.len(), t.len() <= 5 * 10^4`
- `s` and `t` consist of lowercase English letters.

## Hints

<details>
<summary>Hint 1</summary>
If two strings are anagrams, they have the same characters with the same frequencies.
</details>

<details>
<summary>Hint 2</summary>
Sort both strings and compare them, or use a frequency counter.
</details>

<details>
<summary>Hint 3</summary>
Use an array of size 26 to count character frequencies (since only lowercase letters).
</details>

## Function Signature

```rust
impl Solution {
    pub fn is_anagram(s: String, t: String) -> bool {
        
    }
}
```
