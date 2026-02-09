# Solution: Find Minimum

## Complete Runnable Code

```rust
fn find_min(nums: &[i32]) -> Option<i32> {
    if nums.is_empty() {
        return None;
    }
    
    let mut min = nums[0];
    
    for &num in nums.iter().skip(1) {
        if num < min {
            min = num;
        }
    }
    
    Some(min)
}

// Idiomatic Rust
fn find_min_iter(nums: &[i32]) -> Option<i32> {
    nums.iter().copied().min()
}

// Using fold with i32::MAX as initial value
fn find_min_fold(nums: &[i32]) -> Option<i32> {
    if nums.is_empty() {
        return None;
    }
    Some(nums.iter().fold(i32::MAX, |min, &x| if x < min { x } else { min }))
}

fn main() {
    // Test Case 1: Regular array
    let nums1 = vec![3, 1, 4, 1, 5, 9, 2, 6];
    println!("Min of {:?} = {:?}", nums1, find_min(&nums1));
    // Output: Min of [3, 1, 4, 1, 5, 9, 2, 6] = Some(1)
    
    // Test Case 2: Negative numbers
    let nums2 = vec![-5, -2, -8, -1, -9];
    println!("Min of {:?} = {:?}", nums2, find_min(&nums2));
    // Output: Min of [-5, -2, -8, -1, -9] = Some(-9)
    
    // Test Case 3: Single element
    let nums3 = vec![42];
    println!("Min of {:?} = {:?}", nums3, find_min(&nums3));
    // Output: Min of [42] = Some(42)
    
    // Test Case 4: Empty
    let nums4: Vec<i32> = vec![];
    println!("Min of {:?} = {:?}", nums4, find_min(&nums4));
    // Output: Min of [] = None
    
    // Finding both min and max in one pass
    let nums = vec![3, 1, 4, 1, 5, 9, 2, 6];
    let min = find_min(&nums);
    let max = nums.iter().max();
    println!("\nRange: {:?} to {:?}", min, max);
}
```

## How It Works

### Linear Scan Algorithm

```
nums = [3, 1, 4, 1, 5, 9, 2, 6]
min = 3 (first element)

Compare with 1: 1 < 3, min becomes 1 ✓
Compare with 4: 4 > 1, min stays 1
Compare with 1: 1 = 1, min stays 1
Compare with 5: 5 > 1, min stays 1
Compare with 9: 9 > 1, min stays 1
Compare with 2: 2 > 1, min stays 1
Compare with 6: 6 > 1, min stays 1

Return: 1
```

### Visual Tracking

```
Array: [3, 1, 4, 1, 5, 9, 2, 6]
        ↑
min = 3 (initial)

Array: [3, 1, 4, 1, 5, 9, 2, 6]
           ↑
min = 1 (found smaller!)

Array: [3, 1, 4, 1, 5, 9, 2, 6]
                          ... ↑
min = 1 (unchanged till end)
```

### Key Insight

The algorithm is almost identical to Find Maximum:
- Max: `if num > max { max = num }`
- Min: `if num < min { min = num }`

### Finding Both Min and Max

If you need both, do it in one pass:

```rust
fn find_min_max(nums: &[i32]) -> Option<(i32, i32)> {
    if nums.is_empty() {
        return None;
    }
    
    let mut min = nums[0];
    let mut max = nums[0];
    
    for &num in nums.iter().skip(1) {
        if num < min { min = num; }
        if num > max { max = num; }
    }
    
    Some((min, max))
}

// Usage:
// let (min, max) = find_min_max(&nums).unwrap();
```

## Complexity Analysis

- **Time Complexity**: O(n) - We scan each element once
- **Space Complexity**: O(1) - Only one tracking variable
