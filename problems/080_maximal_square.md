# 80. Maximal Square
**Difficulty**: Hard  
**Topics**: Array, Dynamic Programming, Matrix

## Problem Description

Given an `m x n` binary matrix filled with `0`'s and `1`'s, find the largest square containing only `1`'s and return its area.

## Examples

### Example 1:
```
Input: matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
Output: 4
```

### Example 2:
```
Input: matrix = [["0","1"],["1","0"]]
Output: 1
```

### Example 3:
```
Input: matrix = [["0"]]
Output: 0
```

## Constraints

- `m == matrix.len()`
- `n == matrix[i].len()`
- `1 <= m, n <= 300`
- `matrix[i][j]` is `'0'` or `'1'`.

## Hints

<details>
<summary>Hint 1</summary>
dp[i][j] = side length of the largest square with bottom-right corner at (i, j).
</details>

<details>
<summary>Hint 2</summary>
If matrix[i][j] == '1', dp[i][j] = 1 + min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]).
</details>

<details>
<summary>Hint 3</summary>
Track the maximum side length seen. Return max_side^2 as the area.
</details>

## Function Signature

```rust
impl Solution {
    pub fn maximal_square(matrix: Vec<Vec<char>>) -> i32 {
        
    }
}
```
