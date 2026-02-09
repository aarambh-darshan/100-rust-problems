# Solution: Longest Consecutive Sequence

## Complete Runnable Code

```rust
use std::collections::HashSet;

fn longest_consecutive(nums: Vec<i32>) -> i32 {
    let set: HashSet<i32> = nums.into_iter().collect();
    let mut longest = 0;
    
    for &num in &set {
        // Only start counting from sequence start
        if !set.contains(&(num - 1)) {
            let mut current = num;
            let mut length = 1;
            
            while set.contains(&(current + 1)) {
                current += 1;
                length += 1;
            }
            
            longest = longest.max(length);
        }
    }
    
    longest
}

fn main() {
    let test_cases = vec![
        vec![100, 4, 200, 1, 3, 2],
        vec![0, 3, 7, 2, 5, 8, 4, 6, 0, 1],
        vec![1, 2, 0, 1],
    ];
    
    for nums in test_cases {
        let result = longest_consecutive(nums.clone());
        println!("{:?} → longest = {}", nums, result);
    }
}
```

**Output:**
```
[100, 4, 200, 1, 3, 2] → longest = 4
[0, 3, 7, 2, 5, 8, 4, 6, 0, 1] → longest = 9
[1, 2, 0, 1] → longest = 3
```

## How It Works

### Key Insight: Only Process Sequence Starts

A number is a sequence START if `num - 1` is NOT in the set.

```
Set: {100, 4, 200, 1, 3, 2}

100: 99 not in set → START! Count: 100 (length 1)
4:   3 in set → skip (not a start)
200: 199 not in set → START! Count: 200 (length 1)
1:   0 not in set → START! Count: 1,2,3,4 (length 4) ✓
3:   2 in set → skip
2:   1 in set → skip

Longest = 4
```

## Complexity

- **Time**: O(n) - Each number visited at most twice
- **Space**: O(n)
