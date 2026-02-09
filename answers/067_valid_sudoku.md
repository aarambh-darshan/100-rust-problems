# Solution: Valid Sudoku
```rust
use std::collections::HashSet;
impl Solution {
    pub fn is_valid_sudoku(board: Vec<Vec<char>>) -> bool {
        let mut rows = vec![HashSet::new(); 9];
        let mut cols = vec![HashSet::new(); 9];
        let mut boxes = vec![HashSet::new(); 9];
        for i in 0..9 { for j in 0..9 {
            if board[i][j] == '.' { continue; }
            let num = board[i][j];
            let box_idx = (i / 3) * 3 + j / 3;
            if !rows[i].insert(num) || !cols[j].insert(num) || !boxes[box_idx].insert(num) { return false; }
        }}
        true
    }
}
```
**Time**: O(81), **Space**: O(81)
