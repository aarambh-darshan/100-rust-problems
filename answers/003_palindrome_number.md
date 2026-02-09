# Solution: Palindrome Number

## Complete Runnable Code

```rust
fn is_palindrome(x: i32) -> bool {
    // Negative numbers are never palindromes (e.g., -121 reads as 121-)
    // Numbers ending in 0 are not palindromes (except 0 itself)
    if x < 0 || (x % 10 == 0 && x != 0) {
        return false;
    }
    
    let mut num = x;
    let mut reversed = 0;
    
    // Only reverse half of the number
    // We stop when reversed >= num (we've processed half)
    while num > reversed {
        // Take the last digit of num and add to reversed
        reversed = reversed * 10 + num % 10;
        // Remove the last digit from num
        num /= 10;
    }
    
    // For even-length numbers: num == reversed
    // For odd-length numbers: num == reversed / 10 (middle digit ignored)
    num == reversed || num == reversed / 10
}

fn main() {
    // Test Case 1: Palindrome
    println!("121 is palindrome: {}", is_palindrome(121)); // true
    
    // Test Case 2: Negative number
    println!("-121 is palindrome: {}", is_palindrome(-121)); // false
    
    // Test Case 3: Not palindrome
    println!("10 is palindrome: {}", is_palindrome(10)); // false
    
    // Test Case 4: Single digit
    println!("7 is palindrome: {}", is_palindrome(7)); // true
    
    // Test Case 5: Even length palindrome
    println!("1221 is palindrome: {}", is_palindrome(1221)); // true
    
    // Test Case 6: Zero
    println!("0 is palindrome: {}", is_palindrome(0)); // true
}
```

## How It Works

### The Clever Trick: Reverse Only Half

Instead of reversing the entire number (which could overflow), we reverse only HALF:

```
Example: 12321 (odd length)

Step 1: num = 12321, reversed = 0
        Take last digit: 12321 % 10 = 1
        reversed = 0 * 10 + 1 = 1
        num = 12321 / 10 = 1232

Step 2: num = 1232, reversed = 1
        Take last digit: 1232 % 10 = 2
        reversed = 1 * 10 + 2 = 12
        num = 1232 / 10 = 123

Step 3: num = 123, reversed = 12
        Take last digit: 123 % 10 = 3
        reversed = 12 * 10 + 3 = 123
        num = 123 / 10 = 12

Step 4: num = 12, reversed = 123
        Now reversed > num, STOP!

Check: num (12) == reversed / 10 (123 / 10 = 12) ✓ Palindrome!
```

### Visual for Even Length

```
Example: 1221

Step 1: num = 1221, reversed = 1
Step 2: num = 122, reversed = 12
Step 3: num = 12, reversed = 12   (reversed >= num, STOP!)

Check: num (12) == reversed (12) ✓ Palindrome!
```

### Why Check Both Conditions?

```rust
num == reversed || num == reversed / 10
```

- **Even length (1221)**: After halving, `num = 12`, `reversed = 12` → exact match
- **Odd length (12321)**: After halving, `num = 12`, `reversed = 123` → need to ignore middle digit

### Edge Cases Handled

| Input | Why Not Palindrome |
|-------|-------------------|
| -121 | Negative sign at end: "121-" ≠ "-121" |
| 10 | Would read as "01" which isn't same as "10" |

## Complexity Analysis

- **Time Complexity**: O(log₁₀n) - We process half the digits
- **Space Complexity**: O(1) - Only using a few integer variables
