# 26. Length of Last Word
**Difficulty**: Easy  
**Topics**: Strings

## Problem Description

Given a string `s` consisting of words and spaces, return the length of the **last** word in the string.

A **word** is a maximal substring consisting of non-space characters only.

## Examples

### Example 1:
```
Input: s = "Hello World"
Output: 5
Explanation: The last word is "World" with length 5.
```

### Example 2:
```
Input: s = "   fly me   to   the moon  "
Output: 4
Explanation: The last word is "moon" with length 4.
```

### Example 3:
```
Input: s = "luffy is still joyboy"
Output: 6
Explanation: The last word is "joyboy" with length 6.
```

## Constraints

- `1 <= s.len() <= 10^4`
- `s` consists of only English letters and spaces `' '`.
- There will be at least one word in `s`.

## Hints

<details>
<summary>Hint 1</summary>
First, trim any trailing spaces from the string.
</details>

<details>
<summary>Hint 2</summary>
Then find the last space and calculate the length from there to the end.
</details>

<details>
<summary>Hint 3</summary>
In Rust: s.trim().split_whitespace().last().map(|w| w.len()).unwrap_or(0)
</details>

## Function Signature

```rust
impl Solution {
    pub fn length_of_last_word(s: String) -> i32 {
        
    }
}
```
