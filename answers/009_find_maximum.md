# Solution: Find Maximum

## Complete Runnable Code

```rust
fn find_max(nums: &[i32]) -> Option<i32> {
    if nums.is_empty() {
        return None; // Handle empty array
    }
    
    let mut max = nums[0];
    
    for &num in nums.iter().skip(1) {
        if num > max {
            max = num;
        }
    }
    
    Some(max)
}

// Idiomatic Rust using Iterator
fn find_max_iter(nums: &[i32]) -> Option<i32> {
    nums.iter().copied().max()
}

// Using fold
fn find_max_fold(nums: &[i32]) -> Option<i32> {
    nums.iter().copied().reduce(|a, b| if a > b { a } else { b })
}

fn main() {
    // Test Case 1: Regular array
    let nums1 = vec![3, 1, 4, 1, 5, 9, 2, 6];
    println!("Max of {:?} = {:?}", nums1, find_max(&nums1));
    // Output: Max of [3, 1, 4, 1, 5, 9, 2, 6] = Some(9)
    
    // Test Case 2: Negative numbers
    let nums2 = vec![-5, -2, -8, -1, -9];
    println!("Max of {:?} = {:?}", nums2, find_max(&nums2));
    // Output: Max of [-5, -2, -8, -1, -9] = Some(-1)
    
    // Test Case 3: Single element
    let nums3 = vec![42];
    println!("Max of {:?} = {:?}", nums3, find_max(&nums3));
    // Output: Max of [42] = Some(42)
    
    // Test Case 4: Empty array
    let nums4: Vec<i32> = vec![];
    println!("Max of {:?} = {:?}", nums4, find_max(&nums4));
    // Output: Max of [] = None
    
    // Test Case 5: All same elements
    let nums5 = vec![7, 7, 7, 7];
    println!("Max of {:?} = {:?}", nums5, find_max(&nums5));
    // Output: Max of [7, 7, 7, 7] = Some(7)
    
    // Using the value safely
    if let Some(max) = find_max(&nums1) {
        println!("\nThe maximum value is: {}", max);
    }
}
```

## How It Works

### Linear Scan Algorithm

```
nums = [3, 1, 4, 1, 5, 9, 2, 6]
max = 3 (first element)

Compare with 1: 1 < 3, max stays 3
Compare with 4: 4 > 3, max becomes 4
Compare with 1: 1 < 4, max stays 4
Compare with 5: 5 > 4, max becomes 5
Compare with 9: 9 > 5, max becomes 9
Compare with 2: 2 < 9, max stays 9
Compare with 6: 6 < 9, max stays 9

Return: 9
```

### Visual Representation

```
[3, 1, 4, 1, 5, 9, 2, 6]
 ↑
max=3

[3, 1, 4, 1, 5, 9, 2, 6]
    ↑
max=3 (1 < 3, no change)

[3, 1, 4, 1, 5, 9, 2, 6]
       ↑
max=4 (4 > 3, update!)

... continues ...

[3, 1, 4, 1, 5, 9, 2, 6]
                ↑
max=9 (final answer)
```

### Why Return Option<i32>?

In Rust, we handle edge cases properly:
- `Some(value)` when we find a maximum
- `None` when the array is empty

This avoids panics and makes the code safer!

### Using Iterator Methods

```rust
nums.iter().copied().max()
```

- `iter()` - creates an iterator
- `copied()` - converts `&i32` to `i32`
- `max()` - finds maximum, returns `Option<i32>`

### Comparison

| Method | Code Length | Readability |
|--------|-------------|-------------|
| Loop | More code | Very clear |
| Iterator | One line | Idiomatic |
| Fold/Reduce | Medium | Functional style |

## Complexity Analysis

- **Time Complexity**: O(n) - We check each element exactly once
- **Space Complexity**: O(1) - Only using one variable to track max
