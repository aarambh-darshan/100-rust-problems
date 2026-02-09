# Solution: Count Digits

## Complete Runnable Code

```rust
fn count_digits(n: i32) -> i32 {
    if n == 0 {
        return 1; // 0 has 1 digit
    }
    
    let mut num = n.abs(); // Handle negative numbers
    let mut count = 0;
    
    // Remove digits one by one and count
    while num > 0 {
        count += 1;
        num /= 10;
    }
    
    count
}

// Alternative using string conversion
fn count_digits_string(n: i32) -> i32 {
    n.abs().to_string().len() as i32
}

// Alternative using logarithm
fn count_digits_log(n: i32) -> i32 {
    if n == 0 {
        return 1;
    }
    ((n.abs() as f64).log10().floor() as i32) + 1
}

fn main() {
    // Test various numbers
    let test_cases = [0, 1, 9, 10, 99, 100, 12345, -12345, 1000000];
    
    println!("{:>10} | {:>6} | {:>6} | {:>6}", "Number", "Math", "String", "Log");
    println!("{}", "-".repeat(40));
    
    for n in test_cases {
        println!("{:>10} | {:>6} | {:>6} | {:>6}", 
            n, 
            count_digits(n),
            count_digits_string(n),
            count_digits_log(n)
        );
    }
}
```

## How It Works

### Method 1: Division by 10 (Math)

We repeatedly divide by 10 until the number becomes 0:

```
count_digits(12345):

num = 12345, count = 0
num = 1234,  count = 1  (removed 5)
num = 123,   count = 2  (removed 4)
num = 12,    count = 3  (removed 3)
num = 1,     count = 4  (removed 2)
num = 0,     count = 5  (removed 1)

Return: 5
```

### Visual Representation

```
Number: 12345

Step 1: 12345 / 10 = 1234 (remainder 5)  → count = 1
Step 2:  1234 / 10 = 123  (remainder 4)  → count = 2
Step 3:   123 / 10 = 12   (remainder 3)  → count = 3
Step 4:    12 / 10 = 1    (remainder 2)  → count = 4
Step 5:     1 / 10 = 0    (remainder 1)  → count = 5

Final count: 5 digits
```

### Method 2: String Conversion

```rust
n.abs().to_string().len()
```

- Convert number to string: `12345` → `"12345"`
- Get string length: `5`

Simple but less efficient (creates a String allocation).

### Method 3: Logarithm

```
digits = floor(log₁₀(n)) + 1

log₁₀(12345) = 4.091...
floor(4.091) = 4
4 + 1 = 5 digits
```

Why this works:
- log₁₀(10) = 1, log₁₀(99) = 1.99... → 2 digits
- log₁₀(100) = 2, log₁₀(999) = 2.99... → 3 digits

### Edge Cases

| Input | Output | Note |
|-------|--------|------|
| 0 | 1 | Zero has 1 digit |
| -123 | 3 | Use absolute value |
| 1 | 1 | Single digit |
| 1000000 | 7 | Large number |

### Comparison

| Method | Time | Space | Pros |
|--------|------|-------|------|
| Math (division) | O(d) | O(1) | No allocations |
| String | O(d) | O(d) | Simple to write |
| Logarithm | O(1) | O(1) | Constant time |

*d = number of digits*

## Complexity Analysis

- **Time Complexity**: O(log₁₀n) = O(d) where d is the number of digits
- **Space Complexity**: O(1) - Only using integer variables
