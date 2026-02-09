# Solution: Meeting Rooms

## Complete Runnable Code

```rust
fn can_attend_meetings(intervals: Vec<Vec<i32>>) -> bool {
    if intervals.len() <= 1 { return true; }
    
    let mut intervals = intervals;
    intervals.sort_by_key(|i| i[0]);
    
    for i in 1..intervals.len() {
        if intervals[i][0] < intervals[i-1][1] {
            return false;  // Overlap found
        }
    }
    
    true
}

fn main() {
    let test_cases = vec![
        vec![vec![0,30], vec![5,10], vec![15,20]],  // false
        vec![vec![7,10], vec![2,4]],                 // true
    ];
    
    for intervals in test_cases {
        println!("{:?} → {}", intervals, can_attend_meetings(intervals));
    }
}
```

**Output:**
```
[[0, 30], [5, 10], [15, 20]] → false
[[7, 10], [2, 4]] → true
```

## How It Works

Sort by start time, then check if any meeting starts before the previous ends.

```
[0,30], [5,10], [15,20] (sorted by start)
       ↑
  5 < 30 → OVERLAP!
```

## Complexity

- **Time**: O(n log n) for sorting
- **Space**: O(1)
