# Solution: Binary Search

## Complete Runnable Code

```rust
fn search(nums: Vec<i32>, target: i32) -> i32 {
    let mut left = 0i32;
    let mut right = nums.len() as i32 - 1;
    
    while left <= right {
        let mid = left + (right - left) / 2;
        
        match nums[mid as usize].cmp(&target) {
            std::cmp::Ordering::Equal => return mid,
            std::cmp::Ordering::Less => left = mid + 1,
            std::cmp::Ordering::Greater => right = mid - 1,
        }
    }
    
    -1
}

fn main() {
    let nums = vec![-1, 0, 3, 5, 9, 12];
    
    for target in [9, 2, 12, -1, 100] {
        let result = search(nums.clone(), target);
        println!("Search for {} → index {}", target, result);
    }
}
```

**Output:**
```
Search for 9 → index 4
Search for 2 → index -1
Search for 12 → index 5
Search for -1 → index 0
Search for 100 → index -1
```

## How It Works

### Divide and Conquer

Each step eliminates half the search space:

```
nums = [-1, 0, 3, 5, 9, 12], target = 9

Step 1: mid = 2, nums[2] = 3 < 9 → search right [5, 9, 12]
Step 2: mid = 4, nums[4] = 9 = 9 → FOUND!
```

## Complexity

- **Time**: O(log n)
- **Space**: O(1)
