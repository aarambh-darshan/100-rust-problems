# Solution: Climbing Stairs

## Complete Runnable Code

```rust
fn climb_stairs(n: i32) -> i32 {
    if n <= 2 {
        return n;
    }
    
    // We only need to track the last two values
    let mut prev2 = 1;  // ways(n-2)
    let mut prev1 = 2;  // ways(n-1)
    
    for _ in 3..=n {
        let current = prev1 + prev2;  // ways(n) = ways(n-1) + ways(n-2)
        prev2 = prev1;
        prev1 = current;
    }
    
    prev1
}

fn main() {
    // Show results for n = 1 to 10
    println!("Ways to climb stairs:");
    println!("{:>4} | {:>10}", "n", "Ways");
    println!("{}", "-".repeat(18));
    
    for n in 1..=10 {
        println!("{:>4} | {:>10}", n, climb_stairs(n));
    }
    
    // Visualize for n = 4
    println!("\n--- All paths for n=4 ---");
    println!("1+1+1+1");
    println!("1+1+2");
    println!("1+2+1");
    println!("2+1+1");
    println!("2+2");
    println!("Total: 5 ways");
}
```

**Output:**
```
Ways to climb stairs:
   n |       Ways
------------------
   1 |          1
   2 |          2
   3 |          3
   4 |          5
   5 |          8
   6 |         13
   7 |         21
   8 |         34
   9 |         55
  10 |         89
```

## How It Works

### The Key Insight

To reach step `n`, you can come from:
- Step `n-1` (take 1 step)
- Step `n-2` (take 2 steps)

So: `ways(n) = ways(n-1) + ways(n-2)`

This is the **Fibonacci sequence**!

### Base Cases

```
n=1: Only 1 way → [1]
n=2: 2 ways → [1,1] or [2]
```

### Building Up for n=5

```
n=1: 1 way
n=2: 2 ways
n=3: 3 ways (=2+1)
n=4: 5 ways (=3+2)
n=5: 8 ways (=5+3)
```

### Visual Path Tree for n=4

```
Start (step 0)
├── Take 1 step → step 1
│   ├── Take 1 → step 2
│   │   ├── Take 1 → step 3
│   │   │   └── Take 1 → step 4 ✓ (1+1+1+1)
│   │   └── Take 2 → step 4 ✓ (1+1+2)
│   └── Take 2 → step 3
│       └── Take 1 → step 4 ✓ (1+2+1)
└── Take 2 steps → step 2
    ├── Take 1 → step 3
    │   └── Take 1 → step 4 ✓ (2+1+1)
    └── Take 2 → step 4 ✓ (2+2)

Total: 5 paths
```

### Why Not Recursion?

```rust
// DON'T do this - exponential time!
fn climb_stairs_slow(n: i32) -> i32 {
    if n <= 2 { return n; }
    climb_stairs_slow(n-1) + climb_stairs_slow(n-2)
}
```

Same problem as naive Fibonacci - recalculates same values!

### Space Optimization

We only need the last two values, not the entire array:

```rust
// Instead of:
let mut dp = vec![0; n+1];
dp[1] = 1; dp[2] = 2;
for i in 3..=n { dp[i] = dp[i-1] + dp[i-2]; }

// We use:
let (mut prev2, mut prev1) = (1, 2);
for _ in 3..=n { (prev2, prev1) = (prev1, prev1 + prev2); }
```

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass from 3 to n
- **Space Complexity**: O(1) - Only storing two previous values
