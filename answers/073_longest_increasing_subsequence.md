# Solution: Longest Increasing Subsequence
```rust
impl Solution {
    pub fn length_of_lis(nums: Vec<i32>) -> i32 {
        let mut tails = Vec::new();
        for &n in &nums {
            match tails.binary_search(&n) { Ok(_) => {} Err(pos) => { if pos == tails.len() { tails.push(n); } else { tails[pos] = n; } } }
        }
        tails.len() as i32
    }
}
```
**Time**: O(n log n), **Space**: O(n)
