# Solution: Sqrt(x)

## Complete Runnable Code

```rust
fn my_sqrt(x: i32) -> i32 {
    if x < 2 {
        return x;
    }
    
    let x = x as i64;  // Avoid overflow
    let mut left: i64 = 1;
    let mut right: i64 = x / 2;
    
    while left <= right {
        let mid = left + (right - left) / 2;
        let square = mid * mid;
        
        if square == x {
            return mid as i32;
        } else if square < x {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    right as i32  // Floor of square root
}

fn main() {
    // Test cases
    let test_cases = [0, 1, 2, 3, 4, 8, 9, 16, 17, 100, 2147483647];
    
    println!("{:>12} | {:>10} | {:>10}", "Input", "sqrt()", "Check");
    println!("{}", "-".repeat(38));
    
    for x in test_cases {
        let result = my_sqrt(x);
        let check = (result as f64).powi(2);
        println!("{:>12} | {:>10} | {:>10.0}", x, result, check);
    }
}
```

**Output:**
```
       Input |    sqrt() |      Check
--------------------------------------
           0 |         0 |          0
           1 |         1 |          1
           2 |         1 |          1
           3 |         1 |          1
           4 |         2 |          4
           8 |         2 |          4
           9 |         3 |          9
          16 |         4 |         16
          17 |         4 |         16
         100 |        10 |        100
  2147483647 |     46340 | 2147395600
```

## How It Works

### Binary Search for Square Root

We search for the largest integer `m` where `m² ≤ x`.

```
For x = 8:
  Search range: [1, 4]  (since 8/2 = 4)
  
  mid=2: 2² = 4 < 8 → search higher [3, 4]
  mid=3: 3² = 9 > 8 → search lower [3, 2]
  
  left > right, return right = 2 ✓
  (because 2² = 4 ≤ 8 < 9 = 3²)
```

### Step-by-Step for sqrt(8)

```
x = 8, left = 1, right = 4

Iteration 1:
  mid = (1+4)/2 = 2
  2² = 4 < 8
  left = 3

Iteration 2:
  mid = (3+4)/2 = 3
  3² = 9 > 8
  right = 2

left=3 > right=2 → Exit loop
Return: right = 2 ✓
```

### Visual Binary Search

```
x = 17, find floor(√17) ≈ 4.12 → answer is 4

Search space: 1 2 3 4 5 6 7 8
              └───────────────┘
              
mid=4: 4²=16 < 17 → search [5,8]
mid=6: 6²=36 > 17 → search [5,5]
mid=5: 5²=25 > 17 → search [5,4]

left>right → return 4 ✓
```

### Why x/2 as Upper Bound?

For x ≥ 2, √x ≤ x/2:
```
x = 4: √4 = 2 = 4/2 ✓
x = 9: √9 = 3 ≤ 4.5 (9/2) ✓
x = 16: √16 = 4 ≤ 8 (16/2) ✓
```

### Why i64?

`mid * mid` can overflow i32:
```
For x = 2147483647 (i32::MAX)
mid could be ~46340
46340² = 2147395600 (fits in i64, not reliably in i32)
```

## Complexity Analysis

- **Time Complexity**: O(log x) - Binary search halves the range each time
- **Space Complexity**: O(1) - Only using a few variables
