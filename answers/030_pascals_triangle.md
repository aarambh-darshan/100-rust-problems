# Solution: Pascal's Triangle

## Complete Runnable Code

```rust
fn generate(num_rows: i32) -> Vec<Vec<i32>> {
    let num_rows = num_rows as usize;
    let mut triangle = Vec::with_capacity(num_rows);
    
    for row in 0..num_rows {
        let mut current_row = vec![1; row + 1];  // Start with all 1s
        
        // Fill in the middle elements (not first or last)
        for j in 1..row {
            current_row[j] = triangle[row - 1][j - 1] + triangle[row - 1][j];
        }
        
        triangle.push(current_row);
    }
    
    triangle
}

fn main() {
    // Generate Pascal's Triangle with 6 rows
    let triangle = generate(6);
    
    // Pretty print the triangle
    let max_width = triangle.last().map(|r| r.len() * 4).unwrap_or(0);
    
    println!("Pascal's Triangle (6 rows):\n");
    for row in &triangle {
        let row_str: Vec<String> = row.iter().map(|n| format!("{:^4}", n)).collect();
        let padding = (max_width - row.len() * 4) / 2;
        println!("{:>width$}{}", "", row_str.join(""), width = padding);
    }
    
    // Show properties
    println!("\n--- Properties ---");
    println!("Row 4: {:?}", triangle[4]);
    println!("Sum of row 4: {}", triangle[4].iter().sum::<i32>());  // Should be 2^4 = 16
    
    // Show how each element is computed
    println!("\n--- How element [4][2] is computed ---");
    println!("triangle[4][2] = triangle[3][1] + triangle[3][2]");
    println!("            {} = {}        +        {}", 
             triangle[4][2], triangle[3][1], triangle[3][2]);
}
```

**Output:**
```
Pascal's Triangle (6 rows):

          1   
        1   1  
      1   2   1 
    1   3   3   1
  1   4   6   4   1
1   5   10  10  5   1

--- Properties ---
Row 4: [1, 4, 6, 4, 1]
Sum of row 4: 16

--- How element [4][2] is computed ---
triangle[4][2] = triangle[3][1] + triangle[3][2]
            6 = 3        +        3
```

## How It Works

### The Pattern

Each element is the sum of the two elements above it:

```
        1
       1 1
      1 2 1
     1 3 3 1
    1 4 6 4 1
```

### Formula

```
triangle[row][col] = triangle[row-1][col-1] + triangle[row-1][col]
```

Exception: First and last elements of each row are always 1.

### Step-by-Step Construction

```
Row 0: [1]                     (just 1)
Row 1: [1, 1]                  (edges are 1)
Row 2: [1, 1+1, 1] = [1, 2, 1]
Row 3: [1, 1+2, 2+1, 1] = [1, 3, 3, 1]
Row 4: [1, 1+3, 3+3, 3+1, 1] = [1, 4, 6, 4, 1]
```

### Visual Generation

```
Row 0:       [1]
              ↓
Row 1:      [1, 1]
             ↙ ↘
Row 2:    [1, 2, 1]
           ↙↘ ↙↘
Row 3:  [1, 3, 3, 1]
         ↙↘ ↙↘ ↙↘
Row 4:[1, 4, 6, 4, 1]
```

### Properties of Pascal's Triangle

| Property | Example |
|----------|---------|
| Row n has n+1 elements | Row 4 → 5 elements |
| Sum of row n = 2^n | Row 4 sum = 16 = 2^4 |
| Symmetric | [1,4,6,4,1] reads same both ways |
| Contains binomial coefficients | Row n contains C(n,0), C(n,1), ... |

## Complexity Analysis

- **Time Complexity**: O(n²) - We compute n² / 2 elements
- **Space Complexity**: O(n²) - We store the entire triangle
