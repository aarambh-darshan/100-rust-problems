# 81. Number of Islands
**Difficulty**: Hard  
**Topics**: Array, DFS, BFS, Union Find, Matrix

## Problem Description

Given an `m x n` 2D binary grid `grid` which represents a map of `'1'`s (land) and `'0'`s (water), return the number of islands.

An **island** is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

## Examples

### Example 1:
```
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
```

### Example 2:
```
Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3
```

## Constraints

- `m == grid.len()`
- `n == grid[i].len()`
- `1 <= m, n <= 300`
- `grid[i][j]` is `'0'` or `'1'`.

## Hints

<details>
<summary>Hint 1</summary>
Iterate through the grid. When you find a '1', increment island count and mark the entire island as visited.
</details>

<details>
<summary>Hint 2</summary>
Use DFS or BFS to explore and mark all connected '1's as visited (change to '0' or use a visited set).
</details>

<details>
<summary>Hint 3</summary>
Explore in 4 directions: up, down, left, right.
</details>

## Function Signature

```rust
impl Solution {
    pub fn num_islands(grid: Vec<Vec<char>>) -> i32 {
        
    }
}
```
