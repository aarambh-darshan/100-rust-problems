# Solution: Power of Two

## Complete Runnable Code

```rust
fn is_power_of_two(n: i32) -> bool {
    n > 0 && (n & (n - 1)) == 0
}

// Alternative: Loop
fn is_power_of_two_loop(n: i32) -> bool {
    if n <= 0 { return false; }
    let mut num = n;
    while num > 1 {
        if num % 2 != 0 { return false; }
        num /= 2;
    }
    true
}

fn main() {
    println!("Powers of two check:\n");
    
    for n in [0, 1, 2, 3, 4, 5, 8, 15, 16, 17, 1024, -1] {
        let result = is_power_of_two(n);
        let binary = if n > 0 { format!("{:b}", n) } else { "N/A".to_string() };
        println!("{:>6} ({:>12}) → {}", n, binary, result);
    }
}
```

**Output:**
```
Powers of two check:

     0 (         N/A) → false
     1 (           1) → true
     2 (          10) → true
     3 (          11) → false
     4 (         100) → true
     5 (         101) → false
     8 (        1000) → true
    15 (        1111) → false
    16 (       10000) → true
    17 (       10001) → false
  1024 (10000000000) → true
    -1 (         N/A) → false
```

## How It Works

### Binary Pattern of Powers of Two

Powers of two have exactly **one** bit set:

```
1  = 0001
2  = 0010
4  = 0100
8  = 1000
16 = 10000
```

### The Bit Trick: n & (n-1)

For a power of two, `n & (n-1)` equals 0:

```
n = 8:     1000
n-1 = 7:   0111
8 & 7:     0000 ✓

n = 6:     0110
n-1 = 5:   0101
6 & 5:     0100 ✗ (not zero)
```

### Why This Works

`n-1` flips all bits from the rightmost 1-bit onwards:

```
n   = 1000
n-1 = 0111
      ↑↑↑↑ All flipped!

If n has only one 1-bit, AND gives 0.
If n has multiple 1-bits, some remain after AND.
```

### Visual

```
Power of 2 (8):         Not power of 2 (6):
n   = 1000              n   = 0110
n-1 = 0111              n-1 = 0101
      ----                    ----
AND = 0000 ✓            AND = 0100 ✗
```

## Complexity Analysis

- **Time Complexity**: O(1) - Single bitwise operation
- **Space Complexity**: O(1) - No extra space
