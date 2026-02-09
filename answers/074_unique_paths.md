# Solution: Unique Paths
```rust
impl Solution {
    pub fn unique_paths(m: i32, n: i32) -> i32 {
        let mut dp = vec![1; n as usize];
        for _ in 1..m { for j in 1..n as usize { dp[j] += dp[j - 1]; } }
        dp[n as usize - 1]
    }
}
```
**Time**: O(m*n), **Space**: O(n)
