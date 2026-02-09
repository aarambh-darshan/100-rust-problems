# 59. Meeting Rooms
**Difficulty**: Medium  
**Topics**: Arrays, Sorting

## Problem Description

Given an array of meeting time intervals consisting of start and end times `[[s1,e1],[s2,e2],...]` where `s_i < e_i`, determine if a person could attend all meetings.

## Examples

### Example 1:
```
Input: intervals = [[0,30],[5,10],[15,20]]
Output: false
Explanation: The meeting [0,30] overlaps with [5,10] and [15,20].
```

### Example 2:
```
Input: intervals = [[7,10],[2,4]]
Output: true
Explanation: No meetings overlap.
```

## Constraints

- `0 <= intervals.len() <= 10^4`
- `intervals[i].len() == 2`
- `0 <= start_i < end_i <= 10^6`

## Hints

<details>
<summary>Hint 1</summary>
Sort the meetings by their start time.
</details>

<details>
<summary>Hint 2</summary>
Check if any meeting starts before the previous one ends.
</details>

<details>
<summary>Hint 3</summary>
If intervals[i][0] < intervals[i-1][1] for any i, return false.
</details>

## Function Signature

```rust
impl Solution {
    pub fn can_attend_meetings(intervals: Vec<Vec<i32>>) -> bool {
        
    }
}
```
