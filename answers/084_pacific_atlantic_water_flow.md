# Solution: Pacific Atlantic Water Flow
```rust
impl Solution {
    pub fn pacific_atlantic(heights: Vec<Vec<i32>>) -> Vec<Vec<i32>> {
        let (m, n) = (heights.len(), heights[0].len());
        let mut pacific = vec![vec![false; n]; m];
        let mut atlantic = vec![vec![false; n]; m];
        for i in 0..m { Self::dfs(&heights, &mut pacific, i, 0); Self::dfs(&heights, &mut atlantic, i, n-1); }
        for j in 0..n { Self::dfs(&heights, &mut pacific, 0, j); Self::dfs(&heights, &mut atlantic, m-1, j); }
        let mut result = vec![];
        for i in 0..m { for j in 0..n { if pacific[i][j] && atlantic[i][j] { result.push(vec![i as i32, j as i32]); } } }
        result
    }
    fn dfs(h: &[Vec<i32>], visited: &mut [Vec<bool>], i: usize, j: usize) {
        visited[i][j] = true;
        for (di, dj) in [(0,1),(0,-1),(1,0),(-1,0)] {
            let (ni, nj) = (i as i32 + di, j as i32 + dj);
            if ni >= 0 && nj >= 0 && (ni as usize) < h.len() && (nj as usize) < h[0].len() && 
               !visited[ni as usize][nj as usize] && h[ni as usize][nj as usize] >= h[i][j] {
                Self::dfs(h, visited, ni as usize, nj as usize);
            }
        }
    }
}
```
**Time**: O(m*n), **Space**: O(m*n)
