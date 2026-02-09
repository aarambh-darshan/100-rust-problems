# Solution: Valid Anagram

## Complete Runnable Code

```rust
use std::collections::HashMap;

fn is_anagram(s: String, t: String) -> bool {
    if s.len() != t.len() {
        return false;
    }
    
    let mut count: HashMap<char, i32> = HashMap::new();
    
    // Add counts for s, subtract for t
    for c in s.chars() {
        *count.entry(c).or_insert(0) += 1;
    }
    for c in t.chars() {
        *count.entry(c).or_insert(0) -= 1;
    }
    
    // All counts should be zero if anagram
    count.values().all(|&v| v == 0)
}

// Alternative: Sort and compare
fn is_anagram_sort(s: String, t: String) -> bool {
    let mut s_chars: Vec<char> = s.chars().collect();
    let mut t_chars: Vec<char> = t.chars().collect();
    s_chars.sort();
    t_chars.sort();
    s_chars == t_chars
}

fn main() {
    let test_cases = [
        ("anagram", "nagaram"),
        ("rat", "car"),
        ("listen", "silent"),
        ("hello", "world"),
        ("a", "a"),
    ];
    
    println!("{:>12} vs {:>12} → {:>8}", "String 1", "String 2", "Anagram?");
    println!("{}", "-".repeat(40));
    
    for (s, t) in test_cases {
        let result = is_anagram(s.to_string(), t.to_string());
        println!("{:>12} vs {:>12} → {:>8}", s, t, result);
    }
}
```

**Output:**
```
    String 1 vs     String 2 → Anagram?
----------------------------------------
     anagram vs      nagaram →     true
         rat vs          car →    false
      listen vs       silent →     true
       hello vs        world →    false
           a vs            a →     true
```

## How It Works

### What is an Anagram?

An anagram is a word formed by rearranging the letters of another word.
- "listen" ↔ "silent" ✓
- "rat" ↔ "tar" ✓
- "rat" ↔ "car" ✗ (different letters)

### Method 1: Character Counting

```
s = "anagram"
t = "nagaram"

Count for s: {a:3, n:1, g:1, r:1, m:1}
Subtract t:  {a:0, n:0, g:0, r:0, m:0}

All zeros → Anagram ✓
```

### Step-by-Step

```
s = "rat", t = "car"

Add 'r': {r:1}
Add 'a': {r:1, a:1}
Add 't': {r:1, a:1, t:1}

Subtract 'c': {r:1, a:1, t:1, c:-1}
Subtract 'a': {r:1, a:0, t:1, c:-1}
Subtract 'r': {r:0, a:0, t:1, c:-1}

{t:1, c:-1} not all zeros → Not anagram ✗
```

### Method 2: Sort and Compare

```rust
"anagram" → sort → "aaagmnr"
"nagaram" → sort → "aaagmnr"
Equal → Anagram ✓
```

### Comparison

| Method | Time | Space |
|--------|------|-------|
| HashMap counting | O(n) | O(1)* |
| Sorting | O(n log n) | O(n) |

*O(1) because alphabet size is fixed (26 letters)

## Complexity Analysis

- **Time Complexity**: O(n) - Two passes through the strings
- **Space Complexity**: O(1) - HashMap limited to 26 letters
