# Solution: Reverse Integer

## Complete Runnable Code

```rust
fn reverse(x: i32) -> i32 {
    let mut num = x;
    let mut reversed: i32 = 0;
    
    while num != 0 {
        // Get the last digit
        let digit = num % 10;
        
        // Check for overflow BEFORE multiplying
        // i32 range: -2147483648 to 2147483647
        if reversed > i32::MAX / 10 || (reversed == i32::MAX / 10 && digit > 7) {
            return 0;
        }
        if reversed < i32::MIN / 10 || (reversed == i32::MIN / 10 && digit < -8) {
            return 0;
        }
        
        // Build the reversed number
        reversed = reversed * 10 + digit;
        
        // Remove the last digit from original
        num /= 10;
    }
    
    reversed
}

fn main() {
    // Test cases
    let test_cases = [123, -123, 120, 0, 1534236469, -1534236469];
    
    println!("{:>15} | {:>15}", "Input", "Reversed");
    println!("{}", "-".repeat(33));
    
    for n in test_cases {
        println!("{:>15} | {:>15}", n, reverse(n));
    }
    
    // Edge cases
    println!("\n--- Edge Cases ---");
    println!("Max i32: {} → {}", i32::MAX, reverse(i32::MAX));
    println!("Min i32: {} → {}", i32::MIN, reverse(i32::MIN));
}
```

**Expected Output:**
```
          Input |        Reversed
---------------------------------
            123 |             321
           -123 |            -321
            120 |              21
              0 |               0
     1534236469 |               0  (would overflow!)
    -1534236469 |               0  (would overflow!)
```

## How It Works

### Core Algorithm

Extract digits from the end and build reversed number:

```
Original: 123
reversed = 0

Step 1: digit = 123 % 10 = 3
        reversed = 0 * 10 + 3 = 3
        num = 123 / 10 = 12

Step 2: digit = 12 % 10 = 2
        reversed = 3 * 10 + 2 = 32
        num = 12 / 10 = 1

Step 3: digit = 1 % 10 = 1
        reversed = 32 * 10 + 1 = 321
        num = 1 / 10 = 0

Return: 321 ✓
```

### Visual Breakdown

```
Input: 123

      123 → Pop 3 → 12
       ↓
  reversed = 3

       12 → Pop 2 → 1
       ↓
  reversed = 32

        1 → Pop 1 → 0
       ↓
  reversed = 321

Output: 321
```

### Negative Numbers

The modulo operation preserves the sign in Rust:
```
-123 % 10 = -3
-123 / 10 = -12

So -123 reverses to -321 automatically!
```

### Overflow Prevention

**The Critical Check:**
```rust
if reversed > i32::MAX / 10 || (reversed == i32::MAX / 10 && digit > 7) {
    return 0;
}
```

Why `7`? Because `i32::MAX = 2147483647`, and the last digit is 7.

```
i32::MAX = 2147483647
i32::MAX / 10 = 214748364

If reversed = 214748364 and digit = 8:
  214748364 * 10 + 8 = 2147483648  → OVERFLOW!

But digit = 7 is safe:
  214748364 * 10 + 7 = 2147483647  → i32::MAX, exactly fits!
```

### Why Return 0 on Overflow?

The problem specifies: return 0 if the result overflows i32 range.

Example: 1534236469 → would reverse to 9646324351, which > i32::MAX

## Complexity Analysis

- **Time Complexity**: O(log₁₀n) - We process each digit once
- **Space Complexity**: O(1) - Only using a few integer variables
