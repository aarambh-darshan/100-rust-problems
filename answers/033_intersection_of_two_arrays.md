# Solution: Intersection of Two Arrays

## Complete Runnable Code

```rust
use std::collections::HashSet;

fn intersection(nums1: Vec<i32>, nums2: Vec<i32>) -> Vec<i32> {
    let set1: HashSet<i32> = nums1.into_iter().collect();
    let set2: HashSet<i32> = nums2.into_iter().collect();
    
    set1.intersection(&set2).copied().collect()
}

// Alternative: Using filter
fn intersection_filter(nums1: Vec<i32>, nums2: Vec<i32>) -> Vec<i32> {
    let set1: HashSet<i32> = nums1.into_iter().collect();
    nums2.into_iter()
        .filter(|x| set1.contains(x))
        .collect::<HashSet<i32>>()
        .into_iter()
        .collect()
}

fn main() {
    let test_cases = [
        (vec![1, 2, 2, 1], vec![2, 2]),
        (vec![4, 9, 5], vec![9, 4, 9, 8, 4]),
        (vec![1, 2, 3], vec![4, 5, 6]),
        (vec![1, 1, 1], vec![1, 1, 1]),
    ];
    
    for (nums1, nums2) in test_cases {
        let result = intersection(nums1.clone(), nums2.clone());
        println!("{:?} ∩ {:?} = {:?}", nums1, nums2, result);
    }
}
```

**Output:**
```
[1, 2, 2, 1] ∩ [2, 2] = [2]
[4, 9, 5] ∩ [9, 4, 9, 8, 4] = [4, 9]
[1, 2, 3] ∩ [4, 5, 6] = []
[1, 1, 1] ∩ [1, 1, 1] = [1]
```

## How It Works

### Set Intersection

1. Convert both arrays to HashSets (removes duplicates)
2. Find elements that appear in BOTH sets

```
nums1 = [1, 2, 2, 1] → set1 = {1, 2}
nums2 = [2, 2]       → set2 = {2}

Intersection: {2} ∩ {1, 2} = {2}
```

### Visual

```
nums1: [4, 9, 5]
       {4, 9, 5}
           
nums2: [9, 4, 9, 8, 4]
       {9, 4, 8}

       set1 ∩ set2:
       
       {4, 9, 5}
           ∩
       {4, 8, 9}
           =
        {4, 9}
```

## Complexity Analysis

- **Time Complexity**: O(n + m) - Converting to sets and intersection
- **Space Complexity**: O(n + m) - Storing both sets
