# Solution: Valid Parentheses

## Complete Runnable Code

```rust
fn is_valid(s: String) -> bool {
    let mut stack: Vec<char> = Vec::new();
    
    for c in s.chars() {
        match c {
            // Push opening brackets onto stack
            '(' | '[' | '{' => stack.push(c),
            
            // For closing brackets, check if matching opening exists
            ')' => {
                if stack.pop() != Some('(') {
                    return false;
                }
            }
            ']' => {
                if stack.pop() != Some('[') {
                    return false;
                }
            }
            '}' => {
                if stack.pop() != Some('{') {
                    return false;
                }
            }
            _ => {} // Ignore other characters
        }
    }
    
    // Valid only if all opening brackets were matched (stack is empty)
    stack.is_empty()
}

fn main() {
    // Test cases
    let test_cases = [
        "()",
        "()[]{}",
        "(]",
        "([)]",
        "{[]}",
        "",
        "((()))",
        "[",
        "]",
    ];
    
    println!("{:>15} | {:>8}", "Input", "Valid?");
    println!("{}", "-".repeat(27));
    
    for s in test_cases {
        println!("{:>15} | {:>8}", format!("\"{}\"", s), is_valid(s.to_string()));
    }
}
```

**Expected Output:**
```
          Input |   Valid?
---------------------------
           "()" |     true
       "()[]{}" |     true
           "(]" |    false
         "([)]" |    false
         "{[]}" |     true
             "" |     true
       "((()))" |     true
            "[" |    false
            "]" |    false
```

## How It Works

### Stack-Based Matching

**Core Idea**: Opening brackets push to stack, closing brackets pop and check for match.

### Step-by-Step for "{[]}"

```
Input: "{[]}"
Stack: []

char '{': Opening → Push
        Stack: ['{']

char '[': Opening → Push
        Stack: ['{', '[']

char ']': Closing → Pop and check
        Pop: '[' ← matches ']' ✓
        Stack: ['{']

char '}': Closing → Pop and check
        Pop: '{' ← matches '}' ✓
        Stack: []

End: Stack is empty → VALID ✓
```

### Step-by-Step for "([)]" (Invalid!)

```
Input: "([)]"
Stack: []

char '(': Push
        Stack: ['(']

char '[': Push
        Stack: ['(', '[']

char ')': Pop and check
        Pop: '[' ← does NOT match ')' ✗
        Return FALSE immediately!
```

### Visual Stack Operations

```
Input: "(())"

Step 1: '('  →  Stack: [(]
                        ↑ push

Step 2: '('  →  Stack: [(, (]
                           ↑ push

Step 3: ')'  →  Stack: [(]
                        ↑ pop (matched)

Step 4: ')'  →  Stack: []
                        pop (matched)

Final: Empty stack → VALID!
```

### Why Stack Works

A stack enforces **Last-In-First-Out** (LIFO) order:
- The most recent opening bracket must be closed first
- `([)]` is invalid because `[` must close before `(`

### Matching Pairs

| Opening | Closing |
|---------|---------|
| `(` | `)` |
| `[` | `]` |
| `{` | `}` |

### Edge Cases

| Input | Output | Reason |
|-------|--------|--------|
| `""` | true | Empty is valid |
| `"["` | false | Unclosed bracket |
| `"]"` | false | No matching opening |
| `"(())"` | true | Nested valid |
| `"()()"` | true | Sequential valid |

## Complexity Analysis

- **Time Complexity**: O(n) - Process each character once
- **Space Complexity**: O(n) - Stack could hold all opening brackets
