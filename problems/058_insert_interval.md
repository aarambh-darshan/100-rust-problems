# 58. Insert Interval
**Difficulty**: Medium  
**Topics**: Arrays

## Problem Description

You are given an array of non-overlapping intervals `intervals` where `intervals[i] = [start_i, end_i]` represent the start and the end of the `i-th` interval and `intervals` is sorted in ascending order by `start_i`. You are also given an interval `new_interval = [start, end]` that represents the start and end of another interval.

Insert `new_interval` into `intervals` such that `intervals` is still sorted in ascending order by `start_i` and `intervals` still does not have any overlapping intervals (merge overlapping intervals if necessary).

Return `intervals` after the insertion.

## Examples

### Example 1:
```
Input: intervals = [[1,3],[6,9]], new_interval = [2,5]
Output: [[1,5],[6,9]]
```

### Example 2:
```
Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], new_interval = [4,8]
Output: [[1,2],[3,10],[12,16]]
Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].
```

## Constraints

- `0 <= intervals.len() <= 10^4`
- `intervals[i].len() == 2`
- `0 <= start_i <= end_i <= 10^5`
- `intervals` is sorted by `start_i` in ascending order.
- `new_interval.len() == 2`
- `0 <= start <= end <= 10^5`

## Hints

<details>
<summary>Hint 1</summary>
Add all intervals that come before the new interval (no overlap on the left).
</details>

<details>
<summary>Hint 2</summary>
Merge all overlapping intervals with the new interval.
</details>

<details>
<summary>Hint 3</summary>
Add all intervals that come after the merged interval.
</details>

## Function Signature

```rust
impl Solution {
    pub fn insert(intervals: Vec<Vec<i32>>, new_interval: Vec<i32>) -> Vec<Vec<i32>> {
        
    }
}
```
