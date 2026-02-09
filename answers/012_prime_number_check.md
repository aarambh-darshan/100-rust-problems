# Solution: Prime Number Check

## Complete Runnable Code

```rust
fn is_prime(n: i32) -> bool {
    // Numbers less than 2 are not prime
    if n < 2 {
        return false;
    }
    
    // 2 is the only even prime
    if n == 2 {
        return true;
    }
    
    // All other even numbers are not prime
    if n % 2 == 0 {
        return false;
    }
    
    // Check odd divisors up to sqrt(n)
    let limit = (n as f64).sqrt() as i32;
    let mut i = 3;
    
    while i <= limit {
        if n % i == 0 {
            return false;
        }
        i += 2;  // Only check odd numbers
    }
    
    true
}

fn main() {
    // Test first 30 numbers
    println!("Prime numbers from 1 to 30:");
    let primes: Vec<i32> = (1..=30).filter(|&n| is_prime(n)).collect();
    println!("{:?}", primes);
    // Output: [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
    
    // Test specific numbers
    println!("\nTesting specific numbers:");
    let test_cases = [0, 1, 2, 3, 4, 17, 18, 97, 100];
    for n in test_cases {
        println!("{:>3} is prime: {}", n, is_prime(n));
    }
    
    // Count primes up to 100
    let count = (1..=100).filter(|&n| is_prime(n)).count();
    println!("\nNumber of primes from 1-100: {}", count);  // 25
}
```

## How It Works

### What is a Prime Number?

A prime number is:
- Greater than 1
- Only divisible by 1 and itself

Examples:
- Prime: 2, 3, 5, 7, 11, 13, 17, 19, 23...
- Not prime: 0, 1, 4, 6, 8, 9, 10, 12...

### Why Check Only Up to √n?

If n = a × b, then one of them must be ≤ √n

```
Example: 36 = 2 × 18 = 3 × 12 = 4 × 9 = 6 × 6

√36 = 6

If we find no divisor up to 6, there's none above either!
Because: 36 = 4 × 9, and 4 < 6 (we would have found 4)
```

### Step-by-Step for is_prime(17)

```
n = 17
17 >= 2 ✓
17 != 2 (not caught yet)
17 % 2 != 0 (odd) ✓

limit = √17 ≈ 4.12 → 4

Check i = 3: 17 % 3 = 2 (not divisible)
Check i = 5: 5 > 4, stop!

No divisors found → 17 is PRIME ✓
```

### Why Skip Even Numbers?

After checking 2, all other even numbers are NOT prime (divisible by 2).
So we start at 3 and increment by 2: 3, 5, 7, 9, 11...

This cuts our work in half!

### Visual: Prime Check for 100

```
100:
  100 % 2 = 0 → divisible by 2 → NOT PRIME
  (No need to check further!)

97:
  97 % 2 = 1 (odd, continue)
  √97 ≈ 9.8 → check 3, 5, 7, 9
  97 % 3 = 1 ✓
  97 % 5 = 2 ✓
  97 % 7 = 6 ✓
  97 % 9 = 7 ✓
  No divisors → 97 is PRIME!
```

## Complexity Analysis

- **Time Complexity**: O(√n) - We check at most √n divisors
- **Space Complexity**: O(1) - Only using a few variables

### Note on Large Numbers

For very large numbers (cryptography), use probabilistic tests like Miller-Rabin!
