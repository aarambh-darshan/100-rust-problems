# Solution: Rotate Image

## Complete Runnable Code

```rust
fn rotate(matrix: &mut Vec<Vec<i32>>) {
    let n = matrix.len();
    
    // Step 1: Transpose (swap across diagonal)
    for i in 0..n {
        for j in i+1..n {
            let temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }
    
    // Step 2: Reverse each row
    for row in matrix.iter_mut() {
        row.reverse();
    }
}

fn main() {
    let mut matrix = vec![
        vec![1, 2, 3],
        vec![4, 5, 6],
        vec![7, 8, 9],
    ];
    
    println!("Before: {:?}", matrix);
    rotate(&mut matrix);
    println!("After:  {:?}", matrix);
}
```

**Output:**
```
Before: [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
After:  [[7, 4, 1], [8, 5, 2], [9, 6, 3]]
```

## How It Works

**Rotate 90° clockwise = Transpose + Reverse rows**

```
Original:     Transpose:     Reverse rows:
1 2 3         1 4 7          7 4 1
4 5 6    →    2 5 8    →     8 5 2
7 8 9         3 6 9          9 6 3
```

## Complexity

- **Time**: O(n²)
- **Space**: O(1) in-place
