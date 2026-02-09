# Solution: Sort Colors (Dutch National Flag)
```rust
impl Solution {
    pub fn sort_colors(nums: &mut Vec<i32>) {
        let (mut low, mut mid, mut high) = (0, 0, nums.len());
        while mid < high {
            match nums[mid] {
                0 => { nums.swap(low, mid); low += 1; mid += 1; }
                1 => mid += 1,
                2 => { high -= 1; nums.swap(mid, high); }
                _ => unreachable!()
            }
        }
    }
}
```
**Time**: O(n), **Space**: O(1)
