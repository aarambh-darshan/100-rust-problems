# 74. Unique Paths
**Difficulty**: Hard  
**Topics**: Dynamic Programming, Math, Combinatorics

## Problem Description

There is a robot on an `m x n` grid. The robot is initially located at the top-left corner (i.e., `grid[0][0]`). The robot tries to move to the bottom-right corner (i.e., `grid[m - 1][n - 1]`). The robot can only move either down or right at any point in time.

Given the two integers `m` and `n`, return the number of possible unique paths that the robot can take to reach the bottom-right corner.

## Examples

### Example 1:
```
Input: m = 3, n = 7
Output: 28
```

### Example 2:
```
Input: m = 3, n = 2
Output: 3
Explanation: From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down
```

## Constraints

- `1 <= m, n <= 100`

## Hints

<details>
<summary>Hint 1</summary>
dp[i][j] = number of paths to reach cell (i, j) = dp[i-1][j] + dp[i][j-1].
</details>

<details>
<summary>Hint 2</summary>
Base case: dp[0][j] = 1 and dp[i][0] = 1 (only one way to reach any cell in first row/column).
</details>

<details>
<summary>Hint 3</summary>
Math solution: The answer is C(m+n-2, m-1) = (m+n-2)! / ((m-1)! * (n-1)!)
</details>

## Function Signature

```rust
impl Solution {
    pub fn unique_paths(m: i32, n: i32) -> i32 {
        
    }
}
```
