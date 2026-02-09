# 88. Shortest Path in Binary Matrix
**Difficulty**: Hard  
**Topics**: Array, BFS, Matrix

## Problem Description

Given an `n x n` binary matrix `grid`, return the length of the shortest **clear path** in the matrix. If there is no clear path, return `-1`.

A **clear path** in a binary matrix is a path from the **top-left** cell (i.e., `(0, 0)`) to the **bottom-right** cell (i.e., `(n - 1, n - 1)`) such that:

- All the visited cells of the path are `0`.
- All the adjacent cells of the path are **8-directionally** connected (i.e., they are different and they share an edge or a corner).

The **length of a clear path** is the number of visited cells of this path.

## Examples

### Example 1:
```
Input: grid = [[0,1],[1,0]]
Output: 2
```

### Example 2:
```
Input: grid = [[0,0,0],[1,1,0],[1,1,0]]
Output: 4
```

### Example 3:
```
Input: grid = [[1,0,0],[1,1,0],[1,1,0]]
Output: -1
```

## Constraints

- `n == grid.len()`
- `n == grid[i].len()`
- `1 <= n <= 100`
- `grid[i][j]` is `0` or `1`

## Hints

<details>
<summary>Hint 1</summary>
Use BFS - it finds the shortest path in an unweighted grid.
</details>

<details>
<summary>Hint 2</summary>
Start from (0,0) if it's 0, and explore all 8 directions.
</details>

<details>
<summary>Hint 3</summary>
Mark visited cells to avoid revisiting. Return the path length when you reach (n-1, n-1).
</details>

## Function Signature

```rust
use std::collections::VecDeque;

impl Solution {
    pub fn shortest_path_binary_matrix(grid: Vec<Vec<i32>>) -> i32 {
        
    }
}
```
