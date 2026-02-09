# Solution: FizzBuzz

## Complete Runnable Code

```rust
fn fizz_buzz(n: i32) -> Vec<String> {
    let mut result = Vec::new();
    
    for i in 1..=n {
        let output = match (i % 3, i % 5) {
            (0, 0) => String::from("FizzBuzz"), // Divisible by both 3 and 5
            (0, _) => String::from("Fizz"),     // Divisible by 3 only
            (_, 0) => String::from("Buzz"),     // Divisible by 5 only
            _ => i.to_string(),                  // Not divisible by either
        };
        result.push(output);
    }
    
    result
}

fn main() {
    // Test Case 1: n = 3
    let result1 = fizz_buzz(3);
    println!("n=3: {:?}", result1);
    // Output: ["1", "2", "Fizz"]
    
    // Test Case 2: n = 5
    let result2 = fizz_buzz(5);
    println!("n=5: {:?}", result2);
    // Output: ["1", "2", "Fizz", "4", "Buzz"]
    
    // Test Case 3: n = 15
    let result3 = fizz_buzz(15);
    println!("n=15: {:?}", result3);
    // Output: ["1", "2", "Fizz", "4", "Buzz", "Fizz", "7", "8", "Fizz", "Buzz", 
    //          "11", "Fizz", "13", "14", "FizzBuzz"]
}
```

## How It Works

### The Match Pattern

We use Rust's powerful pattern matching on a tuple `(i % 3, i % 5)`:

```
i = 15: (15 % 3, 15 % 5) = (0, 0) → "FizzBuzz"
i = 9:  (9 % 3, 9 % 5)   = (0, 4) → "Fizz"
i = 10: (10 % 3, 10 % 5) = (1, 0) → "Buzz"
i = 7:  (7 % 3, 7 % 5)   = (1, 2) → "7"
```

### Pattern Breakdown

| Pattern | Meaning | Output |
|---------|---------|--------|
| `(0, 0)` | Divisible by 3 AND 5 | "FizzBuzz" |
| `(0, _)` | Divisible by 3 only | "Fizz" |
| `(_, 0)` | Divisible by 5 only | "Buzz" |
| `_` | Neither | The number itself |

### Why Order Matters

The order of patterns is important! `(0, 0)` must come FIRST because:
- 15 matches both `(0, _)` and `(_, 0)`
- Rust matches the FIRST pattern that fits
- So `(0, 0)` catches multiples of 15 before other patterns

### Alternative: If-Else Approach

```rust
fn fizz_buzz_if(n: i32) -> Vec<String> {
    (1..=n).map(|i| {
        if i % 15 == 0 {
            "FizzBuzz".to_string()
        } else if i % 3 == 0 {
            "Fizz".to_string()
        } else if i % 5 == 0 {
            "Buzz".to_string()
        } else {
            i.to_string()
        }
    }).collect()
}
```

### Visual Output

```
 1  →  "1"
 2  →  "2"
 3  →  "Fizz"      (3 ÷ 3 = 1)
 4  →  "4"
 5  →  "Buzz"      (5 ÷ 5 = 1)
 6  →  "Fizz"      (6 ÷ 3 = 2)
 7  →  "7"
 8  →  "8"
 9  →  "Fizz"      (9 ÷ 3 = 3)
10  →  "Buzz"      (10 ÷ 5 = 2)
11  →  "11"
12  →  "Fizz"      (12 ÷ 3 = 4)
13  →  "13"
14  →  "14"
15  →  "FizzBuzz"  (15 ÷ 3 = 5, 15 ÷ 5 = 3)
```

## Complexity Analysis

- **Time Complexity**: O(n) - We iterate through numbers 1 to n once
- **Space Complexity**: O(n) - We store n strings in the result vector
