# Solution: Min Stack

## Complete Runnable Code

```rust
struct MinStack {
    stack: Vec<(i32, i32)>,  // (value, min_so_far)
}

impl MinStack {
    fn new() -> Self {
        MinStack { stack: Vec::new() }
    }
    
    fn push(&mut self, val: i32) {
        let min = self.stack.last()
            .map(|&(_, m)| m.min(val))
            .unwrap_or(val);
        self.stack.push((val, min));
    }
    
    fn pop(&mut self) {
        self.stack.pop();
    }
    
    fn top(&self) -> i32 {
        self.stack.last().unwrap().0
    }
    
    fn get_min(&self) -> i32 {
        self.stack.last().unwrap().1
    }
}

fn main() {
    let mut min_stack = MinStack::new();
    
    println!("MinStack Demo:\n");
    
    let operations = [-2, 0, -3];
    for val in operations {
        min_stack.push(val);
        println!("push({:>3}) → min = {}", val, min_stack.get_min());
    }
    
    println!("\nCurrent min: {}", min_stack.get_min());  // -3
    
    min_stack.pop();
    println!("After pop(): min = {}", min_stack.get_min());  // -2
    
    println!("top() = {}", min_stack.top());  // 0
    println!("getMin() = {}", min_stack.get_min());  // -2
}
```

**Output:**
```
MinStack Demo:

push( -2) → min = -2
push(  0) → min = -2
push( -3) → min = -3

Current min: -3
After pop(): min = -2
top() = 0
getMin() = -2
```

## How It Works

### The Trick: Store Minimum With Each Element

Each stack entry stores `(value, minimum_so_far)`:

```
push(-2): [(-2, -2)]         min = -2
push(0):  [(-2, -2), (0, -2)]   min = -2
push(-3): [(-2, -2), (0, -2), (-3, -3)]  min = -3

pop():    [(-2, -2), (0, -2)]   min = -2
```

### Why This Works

When we pop, the previous minimum is already stored in the element below!

### Visual

```
push -2:  (-2, min=-2)
           ↓
push 0:   (-2, -2) → (0, min=-2)
                      ↓
push -3:  (-2, -2) → (0, -2) → (-3, min=-3)
```

After pop:
```
(-2, -2) → (0, -2)   ← min is still tracked!
            ↑
            current min = -2
```

### All O(1) Operations!

| Operation | Time |
|-----------|------|
| push | O(1) |
| pop | O(1) |
| top | O(1) |
| getMin | O(1) |

## Complexity Analysis

- **Time Complexity**: O(1) for all operations
- **Space Complexity**: O(n) - each element stores an extra min value
