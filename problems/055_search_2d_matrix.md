# 55. Search a 2D Matrix
**Difficulty**: Medium  
**Topics**: Arrays, Binary Search, Matrix

## Problem Description

You are given an `m x n` integer matrix with the following two properties:

- Each row is sorted in non-decreasing order.
- The first integer of each row is greater than the last integer of the previous row.

Given an integer `target`, return `true` if `target` is in `matrix` or `false` otherwise.

You must write a solution in `O(log(m * n))` time complexity.

## Examples

### Example 1:
```
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true
```

### Example 2:
```
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: false
```

## Constraints

- `m == matrix.len()`
- `n == matrix[i].len()`
- `1 <= m, n <= 100`
- `-10^4 <= matrix[i][j], target <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
Treat the 2D matrix as a flattened 1D sorted array.
</details>

<details>
<summary>Hint 2</summary>
Use binary search with virtual indexing: row = index / cols, col = index % cols.
</details>

<details>
<summary>Hint 3</summary>
Alternative: First binary search to find the row, then another to find the column.
</details>

## Function Signature

```rust
impl Solution {
    pub fn search_matrix(matrix: Vec<Vec<i32>>, target: i32) -> bool {
        
    }
}
```
