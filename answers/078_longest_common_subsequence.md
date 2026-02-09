# Solution: Longest Common Subsequence
```rust
impl Solution {
    pub fn longest_common_subsequence(text1: String, text2: String) -> i32 {
        let (t1, t2): (Vec<_>, Vec<_>) = (text1.chars().collect(), text2.chars().collect());
        let mut dp = vec![vec![0; t2.len() + 1]; t1.len() + 1];
        for i in 1..=t1.len() { for j in 1..=t2.len() {
            dp[i][j] = if t1[i-1] == t2[j-1] { dp[i-1][j-1] + 1 } else { dp[i-1][j].max(dp[i][j-1]) };
        }}
        dp[t1.len()][t2.len()]
    }
}
```
**Time**: O(m*n), **Space**: O(m*n)
