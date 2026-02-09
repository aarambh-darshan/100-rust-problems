# Solution: Plus One

## Complete Runnable Code

```rust
fn plus_one(digits: Vec<i32>) -> Vec<i32> {
    let mut digits = digits;
    
    // Iterate from the last digit (rightmost)
    for i in (0..digits.len()).rev() {
        if digits[i] < 9 {
            // No carry needed, just increment and return
            digits[i] += 1;
            return digits;
        }
        // Digit is 9, becomes 0 and carry propagates
        digits[i] = 0;
    }
    
    // If we're here, all digits were 9 (e.g., 999 -> 1000)
    let mut result = vec![1];
    result.append(&mut digits);
    result
}

fn main() {
    // Test cases
    let test_cases = vec![
        vec![1, 2, 3],
        vec![4, 3, 2, 1],
        vec![9],
        vec![9, 9, 9],
        vec![1, 9, 9],
        vec![0],
    ];
    
    for digits in test_cases {
        let result = plus_one(digits.clone());
        println!("{:?} + 1 = {:?}", digits, result);
    }
}
```

**Output:**
```
[1, 2, 3] + 1 = [1, 2, 4]
[4, 3, 2, 1] + 1 = [4, 3, 2, 2]
[9] + 1 = [1, 0]
[9, 9, 9] + 1 = [1, 0, 0, 0]
[1, 9, 9] + 1 = [2, 0, 0]
[0] + 1 = [1]
```

## How It Works

### The Algorithm

We simulate addition like we learned in school - start from the rightmost digit:

```
  123
+   1
-----
  124   (3+1=4, no carry)
```

### Step-by-Step for [1, 2, 3]

```
[1, 2, 3]
         ↑
Index 2: digits[2]=3, 3 < 9
         3 + 1 = 4
Return: [1, 2, 4]
```

### Step-by-Step for [9, 9, 9]

```
[9, 9, 9]
         ↑
Index 2: digits[2]=9, becomes 0 (carry!)
[9, 9, 0]
      ↑
Index 1: digits[1]=9, becomes 0 (carry!)
[9, 0, 0]
   ↑
Index 0: digits[0]=9, becomes 0 (carry!)
[0, 0, 0]

All digits processed, still have carry!
Insert 1 at front: [1, 0, 0, 0]
```

### Visual Carry Propagation

```
    9  9  9
+         1
----------
Carry: ←←←←
   1  0  0  0
```

### Key Insight

- If digit < 9: increment and return immediately (no carry)
- If digit = 9: becomes 0, carry propagates left
- If all digits were 9: result needs one more digit

## Complexity Analysis

- **Time Complexity**: O(n) - At most one pass through all digits
- **Space Complexity**: O(n) - For the result (or O(1) if modifying in place without 999→1000 case)
