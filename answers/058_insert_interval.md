# Solution: Insert Interval
```rust
impl Solution {
    pub fn insert(intervals: Vec<Vec<i32>>, new_interval: Vec<i32>) -> Vec<Vec<i32>> {
        let mut result = Vec::new();
        let (mut start, mut end) = (new_interval[0], new_interval[1]);
        let mut i = 0;
        while i < intervals.len() && intervals[i][1] < start {
            result.push(intervals[i].clone()); i += 1;
        }
        while i < intervals.len() && intervals[i][0] <= end {
            start = start.min(intervals[i][0]);
            end = end.max(intervals[i][1]); i += 1;
        }
        result.push(vec![start, end]);
        result.extend(intervals[i..].iter().cloned());
        result
    }
}
```
**Time**: O(n), **Space**: O(n)
