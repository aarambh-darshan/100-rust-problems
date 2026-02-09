# Solution: Shortest Path in Binary Matrix
```rust
use std::collections::VecDeque;
impl Solution {
    pub fn shortest_path_binary_matrix(mut grid: Vec<Vec<i32>>) -> i32 {
        let n = grid.len();
        if grid[0][0] == 1 || grid[n-1][n-1] == 1 { return -1; }
        let mut queue = VecDeque::from([(0, 0, 1)]);
        grid[0][0] = 1;
        while let Some((i, j, dist)) = queue.pop_front() {
            if i == n-1 && j == n-1 { return dist; }
            for di in -1..=1 { for dj in -1..=1 {
                let (ni, nj) = (i as i32 + di, j as i32 + dj);
                if ni >= 0 && nj >= 0 && (ni as usize) < n && (nj as usize) < n && grid[ni as usize][nj as usize] == 0 {
                    grid[ni as usize][nj as usize] = 1;
                    queue.push_back((ni as usize, nj as usize, dist + 1));
                }
            }}
        }
        -1
    }
}
```
**Time**: O(n²), **Space**: O(n²)
