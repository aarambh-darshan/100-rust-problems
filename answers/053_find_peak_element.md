# Solution: Find Peak Element
```rust
impl Solution {
    pub fn find_peak_element(nums: Vec<i32>) -> i32 {
        let (mut left, mut right) = (0, nums.len() - 1);
        while left < right {
            let mid = left + (right - left) / 2;
            if nums[mid] > nums[mid + 1] { right = mid; }
            else { left = mid + 1; }
        }
        left as i32
    }
}
```
**Time**: O(log n), **Space**: O(1)
