# Solution: Implement Queue

## Complete Runnable Code

```rust
use std::collections::VecDeque;

struct Queue {
    data: VecDeque<i32>,
}

impl Queue {
    fn new() -> Self {
        Queue { data: VecDeque::new() }
    }
    
    fn enqueue(&mut self, value: i32) {
        self.data.push_back(value);
    }
    
    fn dequeue(&mut self) -> Option<i32> {
        self.data.pop_front()
    }
    
    fn front(&self) -> Option<&i32> {
        self.data.front()
    }
    
    fn is_empty(&self) -> bool {
        self.data.is_empty()
    }
    
    fn size(&self) -> usize {
        self.data.len()
    }
}

fn main() {
    let mut queue = Queue::new();
    
    println!("Queue Operations Demo:\n");
    
    // Enqueue elements
    for val in [10, 20, 30, 40] {
        queue.enqueue(val);
        println!("enqueue({}) → queue: {:?}", val, queue.data);
    }
    
    println!("\nQueue state:");
    println!("front: {:?}", queue.front());
    println!("size: {}", queue.size());
    
    // Dequeue elements
    println!("\nDequeue all:");
    while let Some(val) = queue.dequeue() {
        println!("dequeue() → {} | remaining: {:?}", val, queue.data);
    }
}
```

**Output:**
```
Queue Operations Demo:

enqueue(10) → queue: [10]
enqueue(20) → queue: [10, 20]
enqueue(30) → queue: [10, 20, 30]
enqueue(40) → queue: [10, 20, 30, 40]

Queue state:
front: Some(10)
size: 4

Dequeue all:
dequeue() → 10 | remaining: [20, 30, 40]
dequeue() → 20 | remaining: [30, 40]
dequeue() → 30 | remaining: [40]
dequeue() → 40 | remaining: []
```

## How It Works

### Queue: FIFO (First In, First Out)

```
enqueue(10): [10]
enqueue(20): [10, 20]
enqueue(30): [10, 20, 30]
              ↑ front    ↑ back (new items go here)

dequeue(): returns 10, [20, 30]
dequeue(): returns 20, [30]
```

### Visual Queue

```
Front                         Back
  ↓                            ↓
┌────┬────┬────┬────┐
│ 10 │ 20 │ 30 │ 40 │ ← enqueue here
└────┴────┴────┴────┘
  ↑
  dequeue from here
```

### Why VecDeque?

`VecDeque` provides O(1) operations at both ends:

```rust
push_back()  // O(1) - add to back
pop_front()  // O(1) - remove from front
```

Using a regular `Vec` would make `pop_front` O(n)!

## Complexity Analysis

- **Time Complexity**: O(1) for all operations
- **Space Complexity**: O(n) where n is number of elements
