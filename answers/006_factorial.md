# Solution: Factorial

## Complete Runnable Code

```rust
fn factorial(n: i32) -> i64 {
    // Using i64 to handle larger results (n! grows very fast)
    let mut result: i64 = 1;
    
    // Multiply all numbers from 1 to n
    for i in 1..=n as i64 {
        result *= i;
    }
    
    result
}

// Recursive version
fn factorial_recursive(n: i32) -> i64 {
    if n <= 1 {
        1  // Base case: 0! = 1, 1! = 1
    } else {
        n as i64 * factorial_recursive(n - 1)
    }
}

fn main() {
    // Print factorials from 0 to 12
    println!("Factorial Table:");
    println!("{:>4} | {:>15}", "n", "n!");
    println!("{}", "-".repeat(22));
    
    for i in 0..=12 {
        println!("{:>4} | {:>15}", i, factorial(i));
    }
    
    // Test both versions
    println!("\nCompare versions:");
    println!("factorial(5) = {}", factorial(5));          // 120
    println!("factorial_recursive(5) = {}", factorial_recursive(5)); // 120
    
    // Show large factorial
    println!("\nfactorial(20) = {}", factorial(20)); // 2432902008176640000
}
```

## How It Works

### Factorial Definition

```
n! = n × (n-1) × (n-2) × ... × 2 × 1

Examples:
0! = 1 (by definition)
1! = 1
2! = 2 × 1 = 2
3! = 3 × 2 × 1 = 6
4! = 4 × 3 × 2 × 1 = 24
5! = 5 × 4 × 3 × 2 × 1 = 120
```

### Step-by-Step for factorial(5)

```
Iterative:
result = 1
result = 1 × 1 = 1
result = 1 × 2 = 2
result = 2 × 3 = 6
result = 6 × 4 = 24
result = 24 × 5 = 120
Return: 120

Recursive (call stack):
factorial(5) = 5 × factorial(4)
             = 5 × 4 × factorial(3)
             = 5 × 4 × 3 × factorial(2)
             = 5 × 4 × 3 × 2 × factorial(1)
             = 5 × 4 × 3 × 2 × 1
             = 120
```

### Visual Recursion Tree

```
factorial(5)
    │
    5 ×  factorial(4)
              │
              4 × factorial(3)
                      │
                      3 × factorial(2)
                              │
                              2 × factorial(1)
                                      │
                                      1 (base case)

Unwind: 1 → 2 → 6 → 24 → 120
```

### Why i64 Instead of i32?

Factorial grows VERY fast:
```
10! =        3,628,800
12! =      479,001,600
13! =    6,227,020,800  ← Overflows i32 (max: 2,147,483,647)
20! = 2,432,902,008,176,640,000
21! = Overflows i64!
```

### Rust Idiomatic One-Liner

```rust
fn factorial_functional(n: i32) -> i64 {
    (1..=n as i64).product()  // Uses Iterator::product
}
```

### Comparison of Approaches

| Approach | Pros | Cons |
|----------|------|------|
| Iterative | Fast, no stack overflow | Slightly more code |
| Recursive | Clean, mathematical | Stack overflow for large n |
| Functional | One-liner, idiomatic | Less readable for beginners |

## Complexity Analysis

- **Time Complexity**: O(n) - We perform n multiplications
- **Space Complexity**: 
  - Iterative: O(1) - Only one variable
  - Recursive: O(n) - Call stack depth is n
