# Solution: First Unique Character

## Complete Runnable Code

```rust
use std::collections::HashMap;

fn first_uniq_char(s: String) -> i32 {
    let mut count: HashMap<char, i32> = HashMap::new();
    
    // First pass: count occurrences
    for c in s.chars() {
        *count.entry(c).or_insert(0) += 1;
    }
    
    // Second pass: find first character with count 1
    for (i, c) in s.chars().enumerate() {
        if count[&c] == 1 {
            return i as i32;
        }
    }
    
    -1  // No unique character found
}

fn main() {
    let test_cases = [
        "leetcode",
        "loveleetcode",
        "aabb",
        "aabcc",
        "z",
    ];
    
    for s in test_cases {
        let result = first_uniq_char(s.to_string());
        let unique = if result >= 0 {
            format!("'{}' at index {}", s.chars().nth(result as usize).unwrap(), result)
        } else {
            "None".to_string()
        };
        println!("\"{}\" → {}", s, unique);
    }
}
```

**Output:**
```
"leetcode" → 'l' at index 0
"loveleetcode" → 'v' at index 2
"aabb" → None
"aabcc" → 'b' at index 2
"z" → 'z' at index 0
```

## How It Works

### Two-Pass Algorithm

**Pass 1**: Count every character
**Pass 2**: Find first character with count = 1

### Step-by-Step for "leetcode"

```
Pass 1 - Counting:
l:1, e:3, t:1, c:1, o:1, d:1

Pass 2 - Find first unique:
Index 0: 'l' → count[l]=1 ← FOUND! Return 0
```

### Step-by-Step for "loveleetcode"

```
Pass 1 - Counting:
l:2, o:2, v:1, e:4, t:1, c:1, d:1

Pass 2:
Index 0: 'l' → count[l]=2 (not unique)
Index 1: 'o' → count[o]=2 (not unique)
Index 2: 'v' → count[v]=1 ← FOUND! Return 2
```

### Visual

```
"loveleetcode"
 l o v e l e e t c o d e
 ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓
 2 2 1 4 . . . 1 1 . 1 .

     ↑
     First with count=1 → index 2
```

## Complexity Analysis

- **Time Complexity**: O(n) - Two passes through the string
- **Space Complexity**: O(1) - HashMap limited to 26 lowercase letters
