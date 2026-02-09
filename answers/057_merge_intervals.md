# Solution: Merge Intervals
```rust
impl Solution {
    pub fn merge(mut intervals: Vec<Vec<i32>>) -> Vec<Vec<i32>> {
        intervals.sort_by_key(|i| i[0]);
        let mut merged = vec![intervals[0].clone()];
        for interval in intervals.into_iter().skip(1) {
            let last = merged.last_mut().unwrap();
            if interval[0] <= last[1] { last[1] = last[1].max(interval[1]); }
            else { merged.push(interval); }
        }
        merged
    }
}
```
**Time**: O(n log n), **Space**: O(n)
