# Solution: Even or Odd

## Complete Runnable Code

```rust
fn is_even(n: i32) -> bool {
    n % 2 == 0
}

fn is_odd(n: i32) -> bool {
    n % 2 != 0
}

// Using bitwise AND (faster)
fn is_even_bitwise(n: i32) -> bool {
    n & 1 == 0
}

fn is_odd_bitwise(n: i32) -> bool {
    n & 1 == 1
}

fn main() {
    // Test various numbers
    let numbers = [-4, -3, -2, -1, 0, 1, 2, 3, 4, 5];
    
    println!("{:>4} | {:>6} | {:>5}", "Num", "Even?", "Odd?");
    println!("{}", "-".repeat(22));
    
    for n in numbers {
        println!("{:>4} | {:>6} | {:>5}", n, is_even(n), is_odd(n));
    }
    
    // Verify bitwise version gives same results
    println!("\nBitwise check:");
    println!("is_even_bitwise(4) = {}", is_even_bitwise(4));  // true
    println!("is_odd_bitwise(5) = {}", is_odd_bitwise(5));    // true
}
```

## How It Works

### Modulo Method

```
n % 2 gives the remainder when dividing by 2

Even numbers: remainder is 0
  4 % 2 = 0 ✓
  10 % 2 = 0 ✓
  0 % 2 = 0 ✓

Odd numbers: remainder is 1 (or -1 for negatives)
  3 % 2 = 1 ✓
  7 % 2 = 1 ✓
  -3 % 2 = -1 (still != 0, so odd) ✓
```

### Bitwise Method (Faster)

In binary, the last bit determines even/odd:
```
4 in binary:  100  → last bit is 0 → even
5 in binary:  101  → last bit is 1 → odd
6 in binary:  110  → last bit is 0 → even
7 in binary:  111  → last bit is 1 → odd

n & 1 isolates the last bit:
  4 & 1 = 100 & 001 = 000 = 0 (even)
  5 & 1 = 101 & 001 = 001 = 1 (odd)
```

### Visual Binary Explanation

```
Number: 6
Binary: 110
         │
         └─ Last bit: 0 → EVEN

Number: 7
Binary: 111
         │
         └─ Last bit: 1 → ODD
```

### Why Bitwise is Faster

| Operation | CPU Cycles |
|-----------|------------|
| Modulo (%) | ~10-40 cycles |
| Bitwise AND (&) | ~1 cycle |

For most applications, this difference is negligible, but in tight loops processing millions of numbers, bitwise wins!

### Edge Cases

| Input | Even? | Odd? | Note |
|-------|-------|------|------|
| 0 | true | false | Zero is even |
| -2 | true | false | Negative even |
| -3 | false | true | Negative odd |
| 1 | false | true | One is odd |

## Complexity Analysis

- **Time Complexity**: O(1) - Single operation
- **Space Complexity**: O(1) - No extra space
