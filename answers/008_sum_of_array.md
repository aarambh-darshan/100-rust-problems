# Solution: Sum of Array

## Complete Runnable Code

```rust
fn sum_array(nums: Vec<i32>) -> i32 {
    let mut sum = 0;
    
    // Iterate through each element and add to sum
    for num in &nums {
        sum += num;
    }
    
    sum
}

// Idiomatic Rust using Iterator
fn sum_array_iter(nums: Vec<i32>) -> i32 {
    nums.iter().sum()
}

// Using fold (reduce in other languages)
fn sum_array_fold(nums: Vec<i32>) -> i32 {
    nums.iter().fold(0, |acc, &x| acc + x)
}

fn main() {
    // Test Case 1: Regular array
    let nums1 = vec![1, 2, 3, 4, 5];
    println!("Sum of {:?} = {}", nums1, sum_array(nums1.clone()));
    // Output: Sum of [1, 2, 3, 4, 5] = 15
    
    // Test Case 2: Array with negative numbers
    let nums2 = vec![-1, 2, -3, 4, -5];
    println!("Sum of {:?} = {}", nums2, sum_array(nums2.clone()));
    // Output: Sum of [-1, 2, -3, 4, -5] = -3
    
    // Test Case 3: Empty array
    let nums3: Vec<i32> = vec![];
    println!("Sum of {:?} = {}", nums3, sum_array(nums3.clone()));
    // Output: Sum of [] = 0
    
    // Test Case 4: Single element
    let nums4 = vec![42];
    println!("Sum of {:?} = {}", nums4, sum_array(nums4.clone()));
    // Output: Sum of [42] = 42
    
    // Compare all implementations
    let nums = vec![1, 2, 3, 4, 5];
    println!("\nAll methods give same result:");
    println!("Loop:     {}", sum_array(nums.clone()));
    println!("Iterator: {}", sum_array_iter(nums.clone()));
    println!("Fold:     {}", sum_array_fold(nums));
}
```

## How It Works

### Basic Loop Approach

```
nums = [1, 2, 3, 4, 5]
sum = 0

Step 1: sum = 0 + 1 = 1
Step 2: sum = 1 + 2 = 3
Step 3: sum = 3 + 3 = 6
Step 4: sum = 6 + 4 = 10
Step 5: sum = 10 + 5 = 15

Return: 15
```

### Iterator Method

```rust
nums.iter().sum()
```

This is the most idiomatic Rust way:
- `iter()` creates an iterator over the vector
- `sum()` consumes the iterator, adding all elements

### Fold (Reduce) Method

```rust
nums.iter().fold(0, |acc, &x| acc + x)
```

- `0` is the initial accumulator value
- `acc` is the running total
- `x` is the current element
- Returns `acc + x` for each iteration

Visual:
```
fold(0, |acc, x| acc + x)

[1, 2, 3, 4, 5]
 ↓
acc=0, x=1 → 0+1=1
acc=1, x=2 → 1+2=3
acc=3, x=3 → 3+3=6
acc=6, x=4 → 6+4=10
acc=10, x=5 → 10+5=15

Result: 15
```

### Edge Cases

| Input | Output | Note |
|-------|--------|------|
| `[]` | 0 | Empty array sums to 0 |
| `[5]` | 5 | Single element |
| `[-1,-2,-3]` | -6 | Negative numbers |
| `[1,-1,2,-2]` | 0 | Mixed, cancels out |

## Complexity Analysis

- **Time Complexity**: O(n) - We visit each element exactly once
- **Space Complexity**: O(1) - Only using a single sum variable
