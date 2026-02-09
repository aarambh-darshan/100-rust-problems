# Solution: Length of Last Word

## Complete Runnable Code

```rust
fn length_of_last_word(s: String) -> i32 {
    s.trim_end()           // Remove trailing spaces
        .split_whitespace() // Split by whitespace
        .last()             // Get last word
        .map_or(0, |w| w.len() as i32)
}

// Alternative: Manual iteration (more educational)
fn length_of_last_word_manual(s: String) -> i32 {
    let bytes = s.as_bytes();
    let mut length = 0;
    let mut i = bytes.len();
    
    // Skip trailing spaces
    while i > 0 && bytes[i - 1] == b' ' {
        i -= 1;
    }
    
    // Count characters of last word
    while i > 0 && bytes[i - 1] != b' ' {
        length += 1;
        i -= 1;
    }
    
    length
}

fn main() {
    // Test cases
    let test_cases = [
        "Hello World",
        "   fly me   to   the moon  ",
        "luffy is still joyboy",
        "a",
        "  single  ",
        "",
        "   ",
    ];
    
    println!("{:>35} | {:>6}", "Input", "Length");
    println!("{}", "-".repeat(45));
    
    for s in test_cases {
        let len = length_of_last_word(s.to_string());
        println!("{:>35} | {:>6}", format!("\"{}\"", s), len);
    }
}
```

**Output:**
```
                              Input | Length
---------------------------------------------
                      "Hello World" |      5
    "   fly me   to   the moon  " |      4
          "luffy is still joyboy" |      6
                              "a" |      1
                       "  single  " |      6
                               "" |      0
                            "   " |      0
```

## How It Works

### Method 1: Rust Iterator (Idiomatic)

```rust
s.trim_end()           // Remove trailing spaces
    .split_whitespace() // Split into words
    .last()             // Get last word
    .map_or(0, |w| w.len() as i32)  // Get length or 0
```

### Method 2: Manual (From End)

```
"Hello World"
           ↑
           Start from end

Step 1: Skip trailing spaces (none here)
Step 2: Count non-space characters until space or start

"Hello World"
      ↑   ↑
      |   └── Start counting
      └────── Stop at space

Count: 5 ('W', 'o', 'r', 'l', 'd')
```

### Step-by-Step for "   fly me   to   the moon  "

```
"   fly me   to   the moon  "
                           ↑↑
                           trailing spaces

Step 1: Skip trailing spaces
"   fly me   to   the moon  "
                        ↑
                        i points here

Step 2: Count letters
"   fly me   to   the moon  "
                    ↑   ↑
                    |   └── start counting: n, o, o, m
                    └────── stop at space

Count: 4 ('m', 'o', 'o', 'n')
```

### Edge Cases

| Input | Output | Reason |
|-------|--------|--------|
| "" | 0 | Empty string |
| "   " | 0 | Only spaces |
| "a" | 1 | Single character |
| "  a  " | 1 | Word with surrounding spaces |

## Complexity Analysis

- **Time Complexity**: O(n) - In worst case, scan entire string
- **Space Complexity**: O(1) - Only using index variables
