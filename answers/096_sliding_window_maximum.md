# Solution: Sliding Window Maximum
```rust
use std::collections::VecDeque;
impl Solution {
    pub fn max_sliding_window(nums: Vec<i32>, k: i32) -> Vec<i32> {
        let k = k as usize;
        let mut deque: VecDeque<usize> = VecDeque::new();
        let mut result = Vec::new();
        for i in 0..nums.len() {
            while deque.front().map_or(false, |&f| f + k <= i) { deque.pop_front(); }
            while deque.back().map_or(false, |&b| nums[b] < nums[i]) { deque.pop_back(); }
            deque.push_back(i);
            if i >= k - 1 { result.push(nums[*deque.front().unwrap()]); }
        }
        result
    }
}
```
**Time**: O(n), **Space**: O(k)
