# 66. Set Matrix Zeroes
**Difficulty**: Medium  
**Topics**: Arrays, Matrix, Hash Table

## Problem Description

Given an `m x n` integer matrix, if an element is `0`, set its entire row and column to `0`'s.

You must do it **in place**.

## Examples

### Example 1:
```
Input: matrix = [[1,1,1],[1,0,1],[1,1,1]]
Output: [[1,0,1],[0,0,0],[1,0,1]]
```

### Example 2:
```
Input: matrix = [[0,1,2,0],[3,4,5,2],[1,3,1,5]]
Output: [[0,0,0,0],[0,4,5,0],[0,3,1,0]]
```

## Constraints

- `m == matrix.len()`
- `n == matrix[0].len()`
- `1 <= m, n <= 200`
- `-2^31 <= matrix[i][j] <= 2^31 - 1`

## Hints

<details>
<summary>Hint 1</summary>
A straightforward solution uses O(m + n) space to record which rows and columns need to be zeroed.
</details>

<details>
<summary>Hint 2</summary>
For O(1) space, use the first row and first column as markers.
</details>

<details>
<summary>Hint 3</summary>
Use separate variables to track if the first row/column themselves should be zeroed.
</details>

## Function Signature

```rust
impl Solution {
    pub fn set_zeroes(matrix: &mut Vec<Vec<i32>>) {
        
    }
}
```
