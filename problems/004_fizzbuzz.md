# 4. FizzBuzz
**Difficulty**: Easy  
**Topics**: Math, String, Simulation

## Problem Description

Given an integer `n`, return a string array `answer` (1-indexed) where:

- `answer[i] == "FizzBuzz"` if `i` is divisible by 3 and 5.
- `answer[i] == "Fizz"` if `i` is divisible by 3.
- `answer[i] == "Buzz"` if `i` is divisible by 5.
- `answer[i] == i` (as a string) if none of the above conditions are true.

## Examples

### Example 1:
```
Input: n = 3
Output: ["1","2","Fizz"]
```

### Example 2:
```
Input: n = 5
Output: ["1","2","Fizz","4","Buzz"]
```

### Example 3:
```
Input: n = 15
Output: ["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]
```

## Constraints

- `1 <= n <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
Use the modulo operator (%) to check divisibility.
</details>

<details>
<summary>Hint 2</summary>
Check for divisibility by both 3 and 5 first (FizzBuzz), then by 3, then by 5.
</details>

<details>
<summary>Hint 3</summary>
The order of conditions matters! Check the most specific condition (divisible by both) before checking individual conditions.
</details>

## Function Signature

```rust
impl Solution {
    pub fn fizz_buzz(n: i32) -> Vec<String> {
        
    }
}
```
