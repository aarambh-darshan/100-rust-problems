# Solution: Count Vowels

## Complete Runnable Code

```rust
fn count_vowels(s: &str) -> usize {
    let vowels = ['a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'];
    
    s.chars()
        .filter(|c| vowels.contains(c))
        .count()
}

// Alternative: Using match
fn count_vowels_match(s: &str) -> usize {
    s.chars()
        .filter(|c| matches!(c.to_ascii_lowercase(), 'a' | 'e' | 'i' | 'o' | 'u'))
        .count()
}

// Alternative: Manual loop
fn count_vowels_loop(s: &str) -> usize {
    let mut count = 0;
    for c in s.chars() {
        match c.to_ascii_lowercase() {
            'a' | 'e' | 'i' | 'o' | 'u' => count += 1,
            _ => {}
        }
    }
    count
}

fn main() {
    // Test cases
    let test_strings = [
        "hello",
        "HELLO",
        "aeiou",
        "rhythm",
        "The quick brown fox",
        "",
        "12345",
    ];
    
    println!("{:>25} | {:>6}", "String", "Vowels");
    println!("{}", "-".repeat(35));
    
    for s in test_strings {
        println!("{:>25} | {:>6}", format!("\"{}\"", s), count_vowels(s));
    }
    
    // Breakdown of vowels
    let text = "Hello World";
    println!("\n--- Breakdown for \"{}\" ---", text);
    for c in text.chars() {
        let vowels = ['a', 'e', 'i', 'o', 'u'];
        let is_vowel = vowels.contains(&c.to_ascii_lowercase());
        if c.is_alphabetic() {
            println!("'{}' - {}", c, if is_vowel { "VOWEL" } else { "consonant" });
        }
    }
}
```

**Expected Output:**
```
                   String | Vowels
-----------------------------------
                  "hello" |      2
                  "HELLO" |      2
                  "aeiou" |      5
                 "rhythm" |      0
      "The quick brown fox" |      5
                       "" |      0
                  "12345" |      0
```

## How It Works

### What Are Vowels?

The English vowels are: **a, e, i, o, u** (and their uppercase versions)

### Method 1: Array Contains

```rust
let vowels = ['a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'];
s.chars().filter(|c| vowels.contains(c)).count()
```

1. `s.chars()` - creates iterator over characters
2. `filter()` - keeps only vowels
3. `count()` - counts remaining elements

### Method 2: Pattern Matching

```rust
matches!(c.to_ascii_lowercase(), 'a' | 'e' | 'i' | 'o' | 'u')
```

- `to_ascii_lowercase()` normalizes the character
- `matches!` macro checks if value matches pattern

### Step-by-Step for "hello"

```
"hello"

'h' → lowercase 'h' → not a vowel
'e' → lowercase 'e' → VOWEL ✓ (count = 1)
'l' → lowercase 'l' → not a vowel
'l' → lowercase 'l' → not a vowel
'o' → lowercase 'o' → VOWEL ✓ (count = 2)

Total: 2 vowels
```

### Visual

```
"Hello World"
 │││││ │││││
 HVCCC CVCCC
 ↓ ↓   ↓
 │ e   o
 │ (1) (2)
 │
 └─ consonants: H, l, l, W, r, l, d

Count = 2 + 1 = 3 (e, o, o)
Wait: "Hello World" has 'e', 'o', 'o' = 3 vowels!
```

### Edge Cases

| Input | Output | Note |
|-------|--------|------|
| "" | 0 | Empty string |
| "rhythm" | 0 | No vowels |
| "aeiou" | 5 | All vowels |
| "12345" | 0 | Numbers only |
| "AEIOU" | 5 | Uppercase vowels |

## Complexity Analysis

- **Time Complexity**: O(n) - We check each character once
- **Space Complexity**: O(1) - Only using a counter variable
