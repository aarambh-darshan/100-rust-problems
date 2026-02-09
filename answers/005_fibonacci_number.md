# Solution: Fibonacci Number

## Complete Runnable Code

```rust
fn fib(n: i32) -> i32 {
    // Base cases
    if n <= 1 {
        return n;
    }
    
    // We only need to track the last two Fibonacci numbers
    let mut prev2 = 0;  // F(n-2)
    let mut prev1 = 1;  // F(n-1)
    
    // Build up from F(2) to F(n)
    for _ in 2..=n {
        let current = prev1 + prev2;  // F(n) = F(n-1) + F(n-2)
        prev2 = prev1;                 // Shift: F(n-2) becomes old F(n-1)
        prev1 = current;               // Shift: F(n-1) becomes current F(n)
    }
    
    prev1
}

fn main() {
    // Print first 15 Fibonacci numbers
    println!("Fibonacci Sequence:");
    for i in 0..15 {
        println!("F({}) = {}", i, fib(i));
    }
    
    // Test specific cases
    println!("\nTest Cases:");
    println!("fib(0) = {}", fib(0));  // 0
    println!("fib(1) = {}", fib(1));  // 1
    println!("fib(2) = {}", fib(2));  // 1
    println!("fib(10) = {}", fib(10)); // 55
}
```

## How It Works

### Fibonacci Definition

```
F(0) = 0
F(1) = 1
F(n) = F(n-1) + F(n-2) for n > 1
```

Sequence: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...

### Step-by-Step Execution for fib(5)

```
Initial: prev2 = 0 (F0), prev1 = 1 (F1)

i=2: current = 1 + 0 = 1 (F2)
     prev2 = 1, prev1 = 1

i=3: current = 1 + 1 = 2 (F3)
     prev2 = 1, prev1 = 2

i=4: current = 2 + 1 = 3 (F4)
     prev2 = 2, prev1 = 3

i=5: current = 3 + 2 = 5 (F5)
     prev2 = 3, prev1 = 5

Return: 5
```

### Visual Sliding Window

```
Index:    0    1    2    3    4    5
Value:    0    1    1    2    3    5
                         ↑    ↑    ↑
          At i=5:     prev2  prev1  current
```

We're sliding a window of 2 numbers forward!

### Why Not Recursion?

```rust
// DON'T use this - very slow!
fn fib_recursive(n: i32) -> i32 {
    if n <= 1 { n }
    else { fib_recursive(n - 1) + fib_recursive(n - 2) }
}
```

Recursive approach has O(2^n) time complexity due to repeated calculations:
```
fib(5)
├── fib(4)
│   ├── fib(3) ← calculated here
│   └── fib(2)
└── fib(3) ← calculated again!
    ├── fib(2) ← and again
    └── fib(1)
```

### Alternative: Memoization (Top-Down DP)

```rust
use std::collections::HashMap;

fn fib_memo(n: i32, cache: &mut HashMap<i32, i32>) -> i32 {
    if n <= 1 { return n; }
    if let Some(&result) = cache.get(&n) { return result; }
    
    let result = fib_memo(n - 1, cache) + fib_memo(n - 2, cache);
    cache.insert(n, result);
    result
}
```

## Complexity Analysis

| Approach | Time | Space |
|----------|------|-------|
| Iterative (our solution) | O(n) | O(1) |
| Recursive | O(2^n) | O(n) |
| Memoized | O(n) | O(n) |

Our iterative solution is optimal: O(n) time with O(1) space!
