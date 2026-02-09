# Solution: Reverse String

## Complete Runnable Code

```rust
fn reverse_string(s: &mut Vec<char>) {
    let n = s.len();
    
    // Use two pointers: left starts at beginning, right at end
    let mut left = 0;
    let mut right = n.saturating_sub(1); // Handle empty case
    
    // Swap characters until pointers meet in the middle
    while left < right {
        s.swap(left, right);
        left += 1;
        right -= 1;
    }
}

fn main() {
    // Test Case 1
    let mut s1 = vec!['h', 'e', 'l', 'l', 'o'];
    println!("Before: {:?}", s1);
    reverse_string(&mut s1);
    println!("After:  {:?}", s1); // ['o', 'l', 'l', 'e', 'h']
    
    // Test Case 2
    let mut s2 = vec!['H', 'a', 'n', 'n', 'a', 'h'];
    println!("\nBefore: {:?}", s2);
    reverse_string(&mut s2);
    println!("After:  {:?}", s2); // ['h', 'a', 'n', 'n', 'a', 'H']
    
    // Test Case 3 - Single character
    let mut s3 = vec!['a'];
    reverse_string(&mut s3);
    println!("\nSingle char: {:?}", s3); // ['a']
    
    // Test Case 4 - Empty
    let mut s4: Vec<char> = vec![];
    reverse_string(&mut s4);
    println!("Empty: {:?}", s4); // []
}
```

## How It Works

### Two-Pointer Technique

```
Initial:     ['h', 'e', 'l', 'l', 'o']
              ↑                   ↑
             left               right

Step 1:      ['o', 'e', 'l', 'l', 'h']  (swap h ↔ o)
                  ↑           ↑
                 left       right

Step 2:      ['o', 'l', 'l', 'e', 'h']  (swap e ↔ l)
                      ↑   ↑
                     left right

Step 3:      left >= right, STOP!
             (middle element 'l' stays in place)

Result:      ['o', 'l', 'l', 'e', 'h']
```

### Step-by-Step Logic

1. **Initialize two pointers**:
   - `left = 0` (first element)
   - `right = n - 1` (last element)

2. **Swap and move**:
   - Swap `s[left]` with `s[right]`
   - Move `left` forward (+1)
   - Move `right` backward (-1)

3. **Stop condition**:
   - When `left >= right`, we've processed all pairs

### Why This Works

- Each element needs to swap with its "mirror" position
- Position `i` swaps with position `n - 1 - i`
- We only need to go halfway (n/2 swaps) to reverse completely

### Alternative: Using Rust's Built-in

```rust
fn reverse_string_builtin(s: &mut Vec<char>) {
    s.reverse(); // Rust's built-in reverse
}
```

## Complexity Analysis

- **Time Complexity**: O(n) - We visit each element exactly once (n/2 swaps)
- **Space Complexity**: O(1) - Only using two pointer variables, modifying in-place
