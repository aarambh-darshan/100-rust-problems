# Solution: Top K Frequent Elements

## Complete Runnable Code

```rust
use std::collections::HashMap;

fn top_k_frequent(nums: Vec<i32>, k: i32) -> Vec<i32> {
    // Count frequencies
    let mut count: HashMap<i32, usize> = HashMap::new();
    for num in nums {
        *count.entry(num).or_insert(0) += 1;
    }
    
    // Sort by frequency
    let mut pairs: Vec<_> = count.into_iter().collect();
    pairs.sort_by(|a, b| b.1.cmp(&a.1));  // Descending by count
    
    // Take top k
    pairs.into_iter()
        .take(k as usize)
        .map(|(num, _)| num)
        .collect()
}

fn main() {
    let test_cases = vec![
        (vec![1, 1, 1, 2, 2, 3], 2),
        (vec![1], 1),
        (vec![1, 2, 3, 1, 2, 1], 2),
    ];
    
    for (nums, k) in test_cases {
        let result = top_k_frequent(nums.clone(), k);
        println!("nums={:?}, k={} → {:?}", nums, k, result);
    }
}
```

**Output:**
```
nums=[1, 1, 1, 2, 2, 3], k=2 → [1, 2]
nums=[1], k=1 → [1]
nums=[1, 2, 3, 1, 2, 1], k=2 → [1, 2]
```

## How It Works

### Count + Sort

1. Count occurrences with HashMap
2. Sort by count (descending)
3. Take top k elements

```
nums = [1, 1, 1, 2, 2, 3], k = 2

Count: {1: 3, 2: 2, 3: 1}
Sort:  [(1, 3), (2, 2), (3, 1)]
Take 2: [1, 2]
```

## Complexity

- **Time**: O(n log n) for sorting
- **Space**: O(n)
