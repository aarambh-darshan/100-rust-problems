# Solution: Contains Duplicate

## Complete Runnable Code

```rust
use std::collections::HashSet;

fn contains_duplicate(nums: Vec<i32>) -> bool {
    let mut seen = HashSet::new();
    
    for num in nums {
        if !seen.insert(num) {
            return true;  // Already existed
        }
    }
    
    false
}

// Alternative: Compare set size to array size
fn contains_duplicate_set(nums: Vec<i32>) -> bool {
    let set: HashSet<_> = nums.iter().collect();
    set.len() != nums.len()
}

fn main() {
    let test_cases = vec![
        vec![1, 2, 3, 1],
        vec![1, 2, 3, 4],
        vec![1, 1, 1, 3, 3, 4, 3, 2, 4, 2],
        vec![1],
    ];
    
    for nums in test_cases {
        let result = contains_duplicate(nums.clone());
        println!("{:?} → has duplicate: {}", nums, result);
    }
}
```

**Output:**
```
[1, 2, 3, 1] → has duplicate: true
[1, 2, 3, 4] → has duplicate: false
[1, 1, 1, 3, 3, 4, 3, 2, 4, 2] → has duplicate: true
[1] → has duplicate: false
```

## How It Works

### HashSet.insert() Returns Boolean

```rust
// insert() returns true if value was NEW
// returns false if value already EXISTS

seen.insert(1) → true  (new)
seen.insert(2) → true  (new)
seen.insert(1) → false (duplicate!)
```

### Visual

```
nums = [1, 2, 3, 1]

Process 1: seen = {1}
Process 2: seen = {1, 2}
Process 3: seen = {1, 2, 3}
Process 1: Already in set! → return true
```

## Complexity

- **Time**: O(n) - HashSet operations are O(1) average
- **Space**: O(n) - Store up to n elements
