# Solution: Add Binary

## Complete Runnable Code

```rust
fn add_binary(a: String, b: String) -> String {
    let mut result = Vec::new();
    let mut carry = 0;
    
    let a_bytes: Vec<u8> = a.bytes().collect();
    let b_bytes: Vec<u8> = b.bytes().collect();
    
    let mut i = a_bytes.len() as i32 - 1;
    let mut j = b_bytes.len() as i32 - 1;
    
    while i >= 0 || j >= 0 || carry > 0 {
        let mut sum = carry;
        
        if i >= 0 {
            sum += (a_bytes[i as usize] - b'0') as i32;
            i -= 1;
        }
        if j >= 0 {
            sum += (b_bytes[j as usize] - b'0') as i32;
            j -= 1;
        }
        
        result.push(if sum % 2 == 1 { '1' } else { '0' });
        carry = sum / 2;
    }
    
    result.reverse();
    result.into_iter().collect()
}

fn main() {
    // Test cases
    let test_cases = [
        ("11", "1"),
        ("1010", "1011"),
        ("0", "0"),
        ("1", "1"),
        ("1111", "1111"),
    ];
    
    for (a, b) in test_cases {
        let sum = add_binary(a.to_string(), b.to_string());
        println!("{:>6} + {:>6} = {:>8}", a, b, sum);
        
        // Verify with decimal
        let a_dec = i64::from_str_radix(a, 2).unwrap();
        let b_dec = i64::from_str_radix(b, 2).unwrap();
        let sum_dec = i64::from_str_radix(&sum, 2).unwrap();
        println!("{:>6} + {:>6} = {:>8}  (decimal: {} + {} = {})\n", 
                 a, b, sum, a_dec, b_dec, sum_dec);
    }
}
```

**Output:**
```
    11 +      1 =       100
    11 +      1 =      100  (decimal: 3 + 1 = 4)

  1010 +   1011 =    10101
  1010 +   1011 =   10101  (decimal: 10 + 11 = 21)

     0 +      0 =        0
     0 +      0 =       0  (decimal: 0 + 0 = 0)

     1 +      1 =       10
     1 +      1 =      10  (decimal: 1 + 1 = 2)

  1111 +   1111 =    11110
  1111 +   1111 =   11110  (decimal: 15 + 15 = 30)
```

## How It Works

### Binary Addition Rules

```
0 + 0 = 0
0 + 1 = 1
1 + 0 = 1
1 + 1 = 10 (0 with carry 1)
1 + 1 + 1 = 11 (1 with carry 1)
```

### Step-by-Step for "11" + "1"

```
    1 1
  +   1
  -----

Position 0 (rightmost):
  1 + 1 = 2 → write 0, carry 1

Position 1:
  1 + 0 + carry(1) = 2 → write 0, carry 1

Position 2:
  0 + 0 + carry(1) = 1 → write 1, carry 0

Result: 100 (binary) = 4 (decimal)
```

### Visual Column Addition

```
      1  1     (a = 3)
    +    1     (b = 1)
    ------
      carry: 1  1
      ------
    1  0  0    (sum = 4)
```

### The Algorithm

1. Start from rightmost digits
2. Add digits + carry
3. Result digit = sum % 2
4. New carry = sum / 2
5. Move left until all digits and carry processed
6. Reverse the result (we built it backwards)

### Why Reverse?

We build the result from right to left (adding to a Vec), so we need to reverse at the end:

```
Build: ['0', '0', '1']  (least significant first)
Reverse: ['1', '0', '0'] (most significant first)
```

## Complexity Analysis

- **Time Complexity**: O(max(m, n)) - Process all digits of both numbers
- **Space Complexity**: O(max(m, n)) - Store the result
