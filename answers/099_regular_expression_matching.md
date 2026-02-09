# Solution: Regular Expression Matching
```rust
impl Solution {
    pub fn is_match(s: String, p: String) -> bool {
        let (s, p): (Vec<_>, Vec<_>) = (s.chars().collect(), p.chars().collect());
        let (m, n) = (s.len(), p.len());
        let mut dp = vec![vec![false; n + 1]; m + 1];
        dp[0][0] = true;
        for j in 1..=n { if p[j-1] == '*' { dp[0][j] = dp[0][j-2]; } }
        for i in 1..=m { for j in 1..=n {
            if p[j-1] == '*' {
                dp[i][j] = dp[i][j-2] || ((p[j-2] == '.' || p[j-2] == s[i-1]) && dp[i-1][j]);
            } else {
                dp[i][j] = dp[i-1][j-1] && (p[j-1] == '.' || p[j-1] == s[i-1]);
            }
        }}
        dp[m][n]
    }
}
```
**Time**: O(m*n), **Space**: O(m*n)
