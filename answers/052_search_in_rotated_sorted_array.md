# Solution: Search in Rotated Sorted Array
```rust
impl Solution {
    pub fn search(nums: Vec<i32>, target: i32) -> i32 {
        let (mut left, mut right) = (0, nums.len() as i32 - 1);
        while left <= right {
            let mid = left + (right - left) / 2;
            if nums[mid as usize] == target { return mid; }
            if nums[left as usize] <= nums[mid as usize] {
                if nums[left as usize] <= target && target < nums[mid as usize] { right = mid - 1; }
                else { left = mid + 1; }
            } else {
                if nums[mid as usize] < target && target <= nums[right as usize] { left = mid + 1; }
                else { right = mid - 1; }
            }
        }
        -1
    }
}
```
**Time**: O(log n), **Space**: O(1)
