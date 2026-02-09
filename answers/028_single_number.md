# Solution: Single Number

## Complete Runnable Code

```rust
fn single_number(nums: Vec<i32>) -> i32 {
    nums.iter().fold(0, |acc, &num| acc ^ num)
}

// Alternative: More explicit loop
fn single_number_loop(nums: Vec<i32>) -> i32 {
    let mut result = 0;
    for num in nums {
        result ^= num;  // XOR each number
    }
    result
}

fn main() {
    // Test cases
    let test_cases = vec![
        vec![2, 2, 1],
        vec![4, 1, 2, 1, 2],
        vec![1],
        vec![1, 1, 2, 2, 3, 4, 4],
    ];
    
    for nums in test_cases {
        let single = single_number(nums.clone());
        println!("{:?} → single number: {}", nums, single);
    }
    
    // Demonstrate XOR properties
    println!("\n--- XOR Properties ---");
    println!("5 ^ 5 = {} (same number XOR = 0)", 5 ^ 5);
    println!("5 ^ 0 = {} (XOR with 0 = itself)", 5 ^ 0);
    println!("5 ^ 3 ^ 5 = {} (pairs cancel out)", 5 ^ 3 ^ 5);
}
```

**Output:**
```
[2, 2, 1] → single number: 1
[4, 1, 2, 1, 2] → single number: 4
[1] → single number: 1
[1, 1, 2, 2, 3, 4, 4] → single number: 3

--- XOR Properties ---
5 ^ 5 = 0 (same number XOR = 0)
5 ^ 0 = 5 (XOR with 0 = itself)
5 ^ 3 ^ 5 = 3 (pairs cancel out)
```

## How It Works

### XOR Properties

| Property | Example |
|----------|---------|
| A ^ A = 0 | 5 ^ 5 = 0 |
| A ^ 0 = A | 5 ^ 0 = 5 |
| Commutative | A ^ B = B ^ A |
| Associative | (A ^ B) ^ C = A ^ (B ^ C) |

### The Magic

Since every number except one appears twice:
- Pairs XOR to 0
- The single number XORs with 0 to give itself!

### Step-by-Step for [4, 1, 2, 1, 2]

```
Start: result = 0

result = 0 ^ 4 = 4
result = 4 ^ 1 = 5  (binary: 100 ^ 001 = 101)
result = 5 ^ 2 = 7  (binary: 101 ^ 010 = 111)
result = 7 ^ 1 = 6  (binary: 111 ^ 001 = 110)
result = 6 ^ 2 = 4  (binary: 110 ^ 010 = 100)

Final: 4 ✓
```

### Visual XOR Process

```
[4, 1, 2, 1, 2]

Rearranged (conceptually):
[1, 1, 2, 2, 4]

XOR all:
(1 ^ 1) ^ (2 ^ 2) ^ 4
=   0   ^    0    ^ 4
=   0   ^   4
=   4 ✓
```

### Binary XOR Visualization

```
  4:  100
  1:  001
 ---  ---
 ^=   101  (5)
  2:  010
 ---  ---
 ^=   111  (7)
  1:  001
 ---  ---
 ^=   110  (6)
  2:  010
 ---  ---
 ^=   100  (4) ✓
```

### Why XOR is Perfect Here

Every paired number contributes 0 (A ^ A = 0), leaving only the single number!

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass through the array
- **Space Complexity**: O(1) - Only one variable
