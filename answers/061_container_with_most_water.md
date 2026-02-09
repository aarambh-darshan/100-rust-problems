# Solution: Container With Most Water

## Complete Runnable Code

```rust
fn max_area(height: Vec<i32>) -> i32 {
    let mut left = 0;
    let mut right = height.len() - 1;
    let mut max_area = 0;
    
    while left < right {
        let h = height[left].min(height[right]);
        let w = (right - left) as i32;
        max_area = max_area.max(h * w);
        
        if height[left] < height[right] {
            left += 1;
        } else {
            right -= 1;
        }
    }
    
    max_area
}

fn main() {
    let height = vec![1,8,6,2,5,4,8,3,7];
    println!("Max area: {}", max_area(height));  // 49
}
```

**Output:**
```
Max area: 49
```

## How It Works

Two pointers from ends. Move the shorter line inward (can only improve by finding taller line).

```
|       |
|   |   |   |
| | | | | | | |
1 8 6 2 5 4 8 3 7

Best: indices 1 and 8
Area = min(8,7) × 7 = 49
```

## Complexity

- **Time**: O(n)
- **Space**: O(1)
