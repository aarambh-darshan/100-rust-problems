# 17. Count Vowels
**Difficulty**: Easy  
**Topics**: Strings

## Problem Description

Given a string `s`, return the number of vowels in the string.

Vowels are: 'a', 'e', 'i', 'o', 'u' (both lowercase and uppercase).

## Examples

### Example 1:
```
Input: s = "Hello World"
Output: 3
Explanation: The vowels are 'e', 'o', 'o'.
```

### Example 2:
```
Input: s = "AEIOU"
Output: 5
```

### Example 3:
```
Input: s = "xyz"
Output: 0
```

## Constraints

- `1 <= s.len() <= 10^4`
- `s` consists of printable ASCII characters.

## Hints

<details>
<summary>Hint 1</summary>
Iterate through each character and check if it's a vowel.
</details>

<details>
<summary>Hint 2</summary>
Convert characters to lowercase for easier comparison, or check both cases.
</details>

<details>
<summary>Hint 3</summary>
Use Rust's filter and count: s.chars().filter(|c| "aeiouAEIOU".contains(*c)).count()
</details>

## Function Signature

```rust
impl Solution {
    pub fn count_vowels(s: String) -> i32 {
        
    }
}
```
