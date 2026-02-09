# 84. Pacific Atlantic Water Flow
**Difficulty**: Hard  
**Topics**: Array, DFS, BFS, Matrix

## Problem Description

There is an `m x n` rectangular island that borders both the **Pacific Ocean** and **Atlantic Ocean**. The **Pacific Ocean** touches the island's left and top edges, and the **Atlantic Ocean** touches the island's right and bottom edges.

The island is partitioned into a grid of square cells. You are given an `m x n` integer matrix `heights` where `heights[r][c]` represents the **height above sea level** of the cell at coordinate `(r, c)`.

The island receives a lot of rain, and the rain water can flow to neighboring cells directly north, south, east, and west if the neighboring cell's height is **less than or equal to** the current cell's height. Water can flow from any cell adjacent to an ocean into the ocean.

Return a **2D list** of grid coordinates `result` where `result[i] = [ri, ci]` denotes that rain water can flow from cell `(ri, ci)` to **both** the Pacific and Atlantic oceans.

## Examples

### Example 1:
```
Input: heights = [[1,2,2,3,5],[3,2,3,4,4],[2,4,5,3,1],[6,7,1,4,5],[5,1,1,2,4]]
Output: [[0,4],[1,3],[1,4],[2,2],[3,0],[3,1],[4,0]]
```

### Example 2:
```
Input: heights = [[1]]
Output: [[0,0]]
```

## Constraints

- `m == heights.len()`
- `n == heights[r].len()`
- `1 <= m, n <= 200`
- `0 <= heights[r][c] <= 10^5`

## Hints

<details>
<summary>Hint 1</summary>
Instead of flowing from each cell, flow backwards from the oceans.
</details>

<details>
<summary>Hint 2</summary>
Do DFS/BFS from Pacific border cells, marking all reachable cells. Do the same for Atlantic.
</details>

<details>
<summary>Hint 3</summary>
Return cells that are reachable from both oceans.
</details>

## Function Signature

```rust
impl Solution {
    pub fn pacific_atlantic(heights: Vec<Vec<i32>>) -> Vec<Vec<i32>> {
        
    }
}
```
