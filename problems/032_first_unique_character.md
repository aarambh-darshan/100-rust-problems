# 32. First Unique Character in a String
**Difficulty**: Easy  
**Topics**: Strings, HashMap

## Problem Description

Given a string `s`, find the first non-repeating character in it and return its index. If it does not exist, return `-1`.

## Examples

### Example 1:
```
Input: s = "leetcode"
Output: 0
Explanation: The character 'l' at index 0 is the first character that does not occur at any other index.
```

### Example 2:
```
Input: s = "loveleetcode"
Output: 2
Explanation: The character 'v' at index 2 is the first character that does not occur at any other index.
```

### Example 3:
```
Input: s = "aabb"
Output: -1
```

## Constraints

- `1 <= s.len() <= 10^5`
- `s` consists of only lowercase English letters.

## Hints

<details>
<summary>Hint 1</summary>
First, count the frequency of each character in the string.
</details>

<details>
<summary>Hint 2</summary>
Then, iterate through the string again to find the first character with count 1.
</details>

<details>
<summary>Hint 3</summary>
Use an array of size 26 or a HashMap to store character counts.
</details>

## Function Signature

```rust
impl Solution {
    pub fn first_uniq_char(s: String) -> i32 {
        
    }
}
```
