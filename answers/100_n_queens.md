# Solution: N-Queens
```rust
impl Solution {
    pub fn solve_n_queens(n: i32) -> Vec<Vec<String>> {
        let mut result = Vec::new();
        let mut board = vec![vec!['.'; n as usize]; n as usize];
        Self::solve(&mut board, 0, &mut result);
        result
    }
    fn solve(board: &mut Vec<Vec<char>>, row: usize, result: &mut Vec<Vec<String>>) {
        if row == board.len() { result.push(board.iter().map(|r| r.iter().collect()).collect()); return; }
        for col in 0..board.len() {
            if Self::is_safe(board, row, col) {
                board[row][col] = 'Q';
                Self::solve(board, row + 1, result);
                board[row][col] = '.';
            }
        }
    }
    fn is_safe(board: &[Vec<char>], row: usize, col: usize) -> bool {
        for i in 0..row { if board[i][col] == 'Q' { return false; } }
        let (mut i, mut j) = (row as i32 - 1, col as i32 - 1);
        while i >= 0 && j >= 0 { if board[i as usize][j as usize] == 'Q' { return false; } i -= 1; j -= 1; }
        let (mut i, mut j) = (row as i32 - 1, col as i32 + 1);
        while i >= 0 && j < board.len() as i32 { if board[i as usize][j as usize] == 'Q' { return false; } i -= 1; j += 1; }
        true
    }
}
```
**Time**: O(n!), **Space**: O(n²)
