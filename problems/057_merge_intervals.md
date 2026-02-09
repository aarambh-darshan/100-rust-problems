# 57. Merge Intervals
**Difficulty**: Medium  
**Topics**: Arrays, Sorting

## Problem Description

Given an array of `intervals` where `intervals[i] = [start_i, end_i]`, merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

## Examples

### Example 1:
```
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
```

### Example 2:
```
Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
```

## Constraints

- `1 <= intervals.len() <= 10^4`
- `intervals[i].len() == 2`
- `0 <= start_i <= end_i <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
First, sort the intervals by their start time.
</details>

<details>
<summary>Hint 2</summary>
Iterate through sorted intervals. If current interval overlaps with the last merged interval, merge them.
</details>

<details>
<summary>Hint 3</summary>
Two intervals overlap if the start of current is <= the end of the last merged interval.
</details>

## Function Signature

```rust
impl Solution {
    pub fn merge(intervals: Vec<Vec<i32>>) -> Vec<Vec<i32>> {
        
    }
}
```
