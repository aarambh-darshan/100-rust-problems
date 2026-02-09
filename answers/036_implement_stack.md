# Solution: Implement Stack

## Complete Runnable Code

```rust
struct Stack {
    data: Vec<i32>,
}

impl Stack {
    fn new() -> Self {
        Stack { data: Vec::new() }
    }
    
    fn push(&mut self, value: i32) {
        self.data.push(value);
    }
    
    fn pop(&mut self) -> Option<i32> {
        self.data.pop()
    }
    
    fn top(&self) -> Option<&i32> {
        self.data.last()
    }
    
    fn is_empty(&self) -> bool {
        self.data.is_empty()
    }
    
    fn size(&self) -> usize {
        self.data.len()
    }
}

fn main() {
    let mut stack = Stack::new();
    
    println!("Stack Operations Demo:\n");
    
    // Push elements
    for val in [10, 20, 30, 40] {
        stack.push(val);
        println!("push({}) → stack: {:?}", val, stack.data);
    }
    
    println!("\nStack state:");
    println!("top: {:?}", stack.top());
    println!("size: {}", stack.size());
    println!("is_empty: {}\n", stack.is_empty());
    
    // Pop elements
    while let Some(val) = stack.pop() {
        println!("pop() → {} | remaining: {:?}", val, stack.data);
    }
    
    println!("\nFinal state:");
    println!("is_empty: {}", stack.is_empty());
    println!("pop on empty: {:?}", stack.pop());
}
```

**Output:**
```
Stack Operations Demo:

push(10) → stack: [10]
push(20) → stack: [10, 20]
push(30) → stack: [10, 20, 30]
push(40) → stack: [10, 20, 30, 40]

Stack state:
top: Some(40)
size: 4
is_empty: false

pop() → 40 | remaining: [10, 20, 30]
pop() → 30 | remaining: [10, 20]
pop() → 20 | remaining: [10]
pop() → 10 | remaining: []

Final state:
is_empty: true
pop on empty: None
```

## How It Works

### Stack: LIFO (Last In, First Out)

```
push(10): [10]
push(20): [10, 20]
push(30): [10, 20, 30]
               ↑ top

pop(): returns 30, [10, 20]
pop(): returns 20, [10]
pop(): returns 10, []
```

### Visual Stack

```
       │    │
       │ 40 │ ← top (last in, first out)
       │ 30 │
       │ 20 │  
       │ 10 │ ← bottom (first in)
       └────┘
```

### Operations

| Operation | Description | Time |
|-----------|-------------|------|
| push(x) | Add x to top | O(1) |
| pop() | Remove & return top | O(1) |
| top() | See top without removing | O(1) |
| is_empty() | Check if empty | O(1) |
| size() | Get number of elements | O(1) |

## Complexity Analysis

- **Time Complexity**: O(1) for all operations
- **Space Complexity**: O(n) where n is number of elements
