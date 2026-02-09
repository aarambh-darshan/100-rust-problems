# Solution: First Bad Version
```rust
impl Solution {
    pub fn first_bad_version(&self, n: i32) -> i32 {
        let (mut left, mut right) = (1, n);
        while left < right {
            let mid = left + (right - left) / 2;
            if self.is_bad_version(mid) { right = mid; }
            else { left = mid + 1; }
        }
        left
    }
}
```
**Time**: O(log n), **Space**: O(1)
