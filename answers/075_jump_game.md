# Solution: Jump Game
```rust
impl Solution {
    pub fn can_jump(nums: Vec<i32>) -> bool {
        let mut furthest = 0;
        for (i, &n) in nums.iter().enumerate() {
            if i > furthest { return false; }
            furthest = furthest.max(i + n as usize);
        }
        true
    }
}
```
**Time**: O(n), **Space**: O(1)
