# Solution: Product of Array Except Self

## Complete Runnable Code

```rust
fn product_except_self(nums: Vec<i32>) -> Vec<i32> {
    let n = nums.len();
    let mut result = vec![1; n];
    
    // Left products
    let mut left = 1;
    for i in 0..n {
        result[i] = left;
        left *= nums[i];
    }
    
    // Right products (multiply in place)
    let mut right = 1;
    for i in (0..n).rev() {
        result[i] *= right;
        right *= nums[i];
    }
    
    result
}

fn main() {
    let test_cases = vec![
        vec![1, 2, 3, 4],
        vec![-1, 1, 0, -3, 3],
    ];
    
    for nums in test_cases {
        println!("{:?} → {:?}", nums, product_except_self(nums));
    }
}
```

**Output:**
```
[1, 2, 3, 4] → [24, 12, 8, 6]
[-1, 1, 0, -3, 3] → [0, 0, 9, 0, 0]
```

## How It Works

For each element: result = (product of left) × (product of right)

```
[1, 2, 3, 4]

Left pass:  [1, 1, 2, 6]   (product of all elements to the left)
Right pass: [24, 12, 4, 1] (product of all elements to the right)
Result:     [24, 12, 8, 6]
```

## Complexity

- **Time**: O(n)
- **Space**: O(1) excluding output
