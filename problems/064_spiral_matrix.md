# 64. Spiral Matrix
**Difficulty**: Medium  
**Topics**: Arrays, Matrix, Simulation

## Problem Description

Given an `m x n` matrix, return all elements of the matrix in spiral order.

## Examples

### Example 1:
```
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [1,2,3,6,9,8,7,4,5]
```

### Example 2:
```
Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
```

## Constraints

- `m == matrix.len()`
- `n == matrix[i].len()`
- `1 <= m, n <= 10`
- `-100 <= matrix[i][j] <= 100`

## Hints

<details>
<summary>Hint 1</summary>
Use four boundaries: top, bottom, left, right. Move in order: right, down, left, up.
</details>

<details>
<summary>Hint 2</summary>
After traversing each direction, shrink the corresponding boundary.
</details>

<details>
<summary>Hint 3</summary>
Continue until the boundaries cross: while left <= right && top <= bottom.
</details>

## Function Signature

```rust
impl Solution {
    pub fn spiral_order(matrix: Vec<Vec<i32>>) -> Vec<i32> {
        
    }
}
```
