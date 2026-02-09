# Solution: Spiral Matrix

## Complete Runnable Code

```rust
fn spiral_order(matrix: Vec<Vec<i32>>) -> Vec<i32> {
    if matrix.is_empty() { return vec![]; }
    
    let mut result = Vec::new();
    let (mut top, mut bottom) = (0, matrix.len() as i32 - 1);
    let (mut left, mut right) = (0, matrix[0].len() as i32 - 1);
    
    while top <= bottom && left <= right {
        // Right
        for c in left..=right {
            result.push(matrix[top as usize][c as usize]);
        }
        top += 1;
        
        // Down
        for r in top..=bottom {
            result.push(matrix[r as usize][right as usize]);
        }
        right -= 1;
        
        // Left
        if top <= bottom {
            for c in (left..=right).rev() {
                result.push(matrix[bottom as usize][c as usize]);
            }
            bottom -= 1;
        }
        
        // Up
        if left <= right {
            for r in (top..=bottom).rev() {
                result.push(matrix[r as usize][left as usize]);
            }
            left += 1;
        }
    }
    
    result
}

fn main() {
    let matrix = vec![
        vec![1, 2, 3],
        vec![4, 5, 6],
        vec![7, 8, 9],
    ];
    
    println!("{:?}", spiral_order(matrix));
}
```

**Output:**
```
[1, 2, 3, 6, 9, 8, 7, 4, 5]
```

## How It Works

Use 4 boundaries (top, bottom, left, right), spiral inward.

```
1 → 2 → 3
        ↓
4 → 5   6
↑       ↓
7 ← 8 ← 9
```

## Complexity

- **Time**: O(m × n)
- **Space**: O(1) excluding output
