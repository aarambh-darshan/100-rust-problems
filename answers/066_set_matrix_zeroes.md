# Solution: Set Matrix Zeroes
```rust
impl Solution {
    pub fn set_zeroes(matrix: &mut Vec<Vec<i32>>) {
        let (m, n) = (matrix.len(), matrix[0].len());
        let (mut first_row, mut first_col) = (false, false);
        for i in 0..m { if matrix[i][0] == 0 { first_col = true; } }
        for j in 0..n { if matrix[0][j] == 0 { first_row = true; } }
        for i in 1..m { for j in 1..n { if matrix[i][j] == 0 { matrix[i][0] = 0; matrix[0][j] = 0; } } }
        for i in 1..m { for j in 1..n { if matrix[i][0] == 0 || matrix[0][j] == 0 { matrix[i][j] = 0; } } }
        if first_col { for i in 0..m { matrix[i][0] = 0; } }
        if first_row { for j in 0..n { matrix[0][j] = 0; } }
    }
}
```
**Time**: O(m*n), **Space**: O(1)
