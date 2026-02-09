# Solution: Edit Distance
```rust
impl Solution {
    pub fn min_distance(word1: String, word2: String) -> i32 {
        let (m, n) = (word1.len(), word2.len());
        let (w1, w2): (Vec<_>, Vec<_>) = (word1.chars().collect(), word2.chars().collect());
        let mut dp = vec![vec![0; n + 1]; m + 1];
        for i in 0..=m { dp[i][0] = i as i32; }
        for j in 0..=n { dp[0][j] = j as i32; }
        for i in 1..=m { for j in 1..=n {
            dp[i][j] = if w1[i-1] == w2[j-1] { dp[i-1][j-1] } else { 1 + dp[i-1][j-1].min(dp[i-1][j]).min(dp[i][j-1]) };
        }}
        dp[m][n]
    }
}
```
**Time**: O(m*n), **Space**: O(m*n)
