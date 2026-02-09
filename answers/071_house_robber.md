# Solution: House Robber
```rust
impl Solution {
    pub fn rob(nums: Vec<i32>) -> i32 {
        let (mut prev2, mut prev1) = (0, 0);
        for &n in &nums { let curr = prev1.max(prev2 + n); prev2 = prev1; prev1 = curr; }
        prev1
    }
}
```
**Time**: O(n), **Space**: O(1)
