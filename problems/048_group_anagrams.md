# 48. Group Anagrams
**Difficulty**: Medium  
**Topics**: Arrays, HashMap, String, Sorting

## Problem Description

Given an array of strings `strs`, group **the anagrams** together. You can return the answer in **any order**.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Examples

### Example 1:
```
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

### Example 2:
```
Input: strs = [""]
Output: [[""]]
```

### Example 3:
```
Input: strs = ["a"]
Output: [["a"]]
```

## Constraints

- `1 <= strs.len() <= 10^4`
- `0 <= strs[i].len() <= 100`
- `strs[i]` consists of lowercase English letters.

## Hints

<details>
<summary>Hint 1</summary>
Two strings are anagrams if and only if their sorted character sequences are equal.
</details>

<details>
<summary>Hint 2</summary>
Use a HashMap where the key is the sorted string (or character count) and the value is a list of anagrams.
</details>

<details>
<summary>Hint 3</summary>
For each string, sort it (or count characters) to get the key, then add to the corresponding group.
</details>

## Function Signature

```rust
use std::collections::HashMap;

impl Solution {
    pub fn group_anagrams(strs: Vec<String>) -> Vec<Vec<String>> {
        
    }
}
```
