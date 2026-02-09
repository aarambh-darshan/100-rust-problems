# Solution: Maximum Subarray

## Complete Runnable Code

```rust
fn max_sub_array(nums: Vec<i32>) -> i32 {
    let mut max_sum = nums[0];
    let mut current_sum = nums[0];
    
    for &num in &nums[1..] {
        // Either extend previous subarray or start new one
        current_sum = num.max(current_sum + num);
        max_sum = max_sum.max(current_sum);
    }
    
    max_sum
}

fn main() {
    let test_cases = vec![
        vec![-2, 1, -3, 4, -1, 2, 1, -5, 4],
        vec![1],
        vec![5, 4, -1, 7, 8],
    ];
    
    for nums in test_cases {
        println!("{:?} → {}", nums, max_sub_array(nums));
    }
}
```

**Output:**
```
[-2, 1, -3, 4, -1, 2, 1, -5, 4] → 6
[1] → 1
[5, 4, -1, 7, 8] → 23
```

## How It Works

Kadane's Algorithm: At each position, choose to extend or start fresh.

```
[-2, 1, -3, 4, -1, 2, 1, -5, 4]

current: -2 → 1 → -2 → 4 → 3 → 5 → 6 → 1 → 5
max:     -2 → 1 → 1 → 4 → 4 → 5 → 6 → 6 → 6

Best subarray: [4, -1, 2, 1] = 6
```

## Complexity

- **Time**: O(n)
- **Space**: O(1)
