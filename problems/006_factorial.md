# 6. Factorial
**Difficulty**: Easy  
**Topics**: Math, Recursion

## Problem Description

Given a non-negative integer `n`, return the factorial of `n`.

The factorial of `n` (denoted as `n!`) is the product of all positive integers less than or equal to `n`.

```
n! = n × (n-1) × (n-2) × ... × 2 × 1
0! = 1 (by definition)
```

## Examples

### Example 1:
```
Input: n = 5
Output: 120
Explanation: 5! = 5 × 4 × 3 × 2 × 1 = 120
```

### Example 2:
```
Input: n = 3
Output: 6
Explanation: 3! = 3 × 2 × 1 = 6
```

### Example 3:
```
Input: n = 0
Output: 1
Explanation: 0! = 1 by definition
```

## Constraints

- `0 <= n <= 12`
- The answer fits in a 32-bit integer

## Hints

<details>
<summary>Hint 1</summary>
The base case for factorial is: 0! = 1 and 1! = 1
</details>

<details>
<summary>Hint 2</summary>
You can solve this iteratively by multiplying numbers from 1 to n, or recursively using n! = n × (n-1)!
</details>

<details>
<summary>Hint 3</summary>
For the iterative approach, start with result = 1 and multiply by each number from 2 to n.
</details>

## Function Signature

```rust
impl Solution {
    pub fn factorial(n: i32) -> i32 {
        
    }
}
```
