# Solution: Swap Two Numbers

## Complete Runnable Code

```rust
// Method 1: Using a temporary variable
fn swap_with_temp(a: &mut i32, b: &mut i32) {
    let temp = *a;
    *a = *b;
    *b = temp;
}

// Method 2: Using tuple destructuring (Rust idiomatic)
fn swap_tuple(a: &mut i32, b: &mut i32) {
    (*a, *b) = (*b, *a);
}

// Method 3: Using XOR (no extra variable)
fn swap_xor(a: &mut i32, b: &mut i32) {
    if a != b {  // Avoid issues when a and b point to same location
        *a ^= *b;
        *b ^= *a;
        *a ^= *b;
    }
}

// Method 4: Using arithmetic (no extra variable)
fn swap_arithmetic(a: &mut i32, b: &mut i32) {
    *a = *a + *b;
    *b = *a - *b;
    *a = *a - *b;
}

// Method 5: Using std::mem::swap (recommended)
fn swap_std(a: &mut i32, b: &mut i32) {
    std::mem::swap(a, b);
}

fn main() {
    // Test all swap methods
    let test = || {
        let (mut a, mut b) = (5, 10);
        (a, b)
    };
    
    // Method 1: Temp variable
    let (mut a, mut b) = test();
    println!("Before: a={}, b={}", a, b);
    swap_with_temp(&mut a, &mut b);
    println!("After (temp): a={}, b={}\n", a, b);
    
    // Method 2: Tuple
    let (mut a, mut b) = test();
    swap_tuple(&mut a, &mut b);
    println!("After (tuple): a={}, b={}", a, b);
    
    // Method 3: XOR
    let (mut a, mut b) = test();
    swap_xor(&mut a, &mut b);
    println!("After (XOR): a={}, b={}", a, b);
    
    // Method 4: Arithmetic
    let (mut a, mut b) = test();
    swap_arithmetic(&mut a, &mut b);
    println!("After (arithmetic): a={}, b={}", a, b);
    
    // Method 5: std::mem::swap
    let (mut a, mut b) = test();
    swap_std(&mut a, &mut b);
    println!("After (std): a={}, b={}", a, b);
}
```

## How It Works

### Method 1: Temporary Variable (Classic)

```
a = 5, b = 10

temp = a       → temp = 5
a = b          → a = 10
b = temp       → b = 5

Result: a = 10, b = 5 ✓
```

### Method 2: Tuple Destructuring (Rust Magic!)

```rust
(a, b) = (b, a);
```

Rust evaluates the right side first, then assigns:
1. Create temporary tuple (10, 5)
2. Destructure into a=10, b=5

### Method 3: XOR Swap (Bit Manipulation)

```
a = 5  (binary: 0101)
b = 10 (binary: 1010)

Step 1: a ^= b    a = 0101 ^ 1010 = 1111 (15)
Step 2: b ^= a    b = 1010 ^ 1111 = 0101 (5)
Step 3: a ^= b    a = 1111 ^ 0101 = 1010 (10)

Result: a = 10, b = 5 ✓
```

**Why XOR works:**
- `A ^ A = 0` (XOR with self = 0)
- `A ^ 0 = A` (XOR with 0 = unchanged)
- XOR is reversible!

### Method 4: Arithmetic Swap

```
a = 5, b = 10

Step 1: a = a + b = 15
Step 2: b = a - b = 5      (recovers original a)
Step 3: a = a - b = 10     (recovers original b)

Result: a = 10, b = 5 ✓
```

⚠️ **Warning**: Can overflow for large numbers!

### Comparison

| Method | Extra Space | Pros | Cons |
|--------|-------------|------|------|
| Temp variable | O(1) | Simple, safe | Uses extra variable |
| Tuple | O(1) | Idiomatic Rust | Rust-specific |
| XOR | O(1) | No extra variable | Confusing, same-address bug |
| Arithmetic | O(1) | Classic trick | Can overflow |
| std::mem::swap | O(1) | Standard, safe | Needs import |

### Recommendation

Use `std::mem::swap` or tuple destructuring in Rust — they're safe and idiomatic!

## Complexity Analysis

- **Time Complexity**: O(1) - Constant time for all methods
- **Space Complexity**: O(1) - Constant space (or one temp variable)
