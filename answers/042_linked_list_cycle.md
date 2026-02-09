# Solution: Linked List Cycle

## Complete Runnable Code

```rust
// Note: True cycle detection requires shared references (Rc<RefCell<>>).
// This educational example demonstrates the Floyd's algorithm concept.

fn has_cycle_demo() {
    println!("Floyd's Cycle Detection Algorithm (Tortoise and Hare)\n");
    
    // Simulate with array indices
    // Array: [3, 2, 0, -4] where each value points to next index
    // Cycle: 3->2->0->2 (index 1 points back to itself via 2)
    
    let nodes = vec![(3, 1), (2, 2), (0, 3), (-4, 1)]; // (val, next_index)
    //                       ^----- cycle back to index 1
    
    let mut slow = 0usize;
    let mut fast = 0usize;
    let mut has_cycle = false;
    
    println!("Simulating cycle detection:");
    for step in 0..10 {
        slow = nodes[slow].1;
        fast = nodes[nodes[fast].1].1;  // Move twice
        
        println!("Step {}: slow at index {}, fast at index {}", 
                 step + 1, slow, fast);
        
        if slow == fast {
            println!("\n🔄 Cycle detected! Both pointers met at index {}", slow);
            has_cycle = true;
            break;
        }
    }
    
    if !has_cycle {
        println!("No cycle (shouldn't reach here in this example)");
    }
}

fn main() {
    has_cycle_demo();
}
```

**Output:**
```
Floyd's Cycle Detection Algorithm (Tortoise and Hare)

Simulating cycle detection:
Step 1: slow at index 1, fast at index 2
Step 2: slow at index 2, fast at index 1
Step 3: slow at index 3, fast at index 3

🔄 Cycle detected! Both pointers met at index 3
```

## How It Works

### Floyd's Cycle Detection

- **Slow pointer**: Moves 1 step at a time
- **Fast pointer**: Moves 2 steps at a time

If there's a cycle, fast will eventually catch up to slow!

### Why It Works

```
In a cycle, fast pointer gains 1 step per iteration.
Eventually it "laps" the slow pointer.

           ┌───────┐
           ↓       │
     1 → 2 → 3 → 4 ┘
         ↑
         Entry point
```

### Visual

```
Start: S=F at head

Step 1: S moves 1, F moves 2
Step 2: S moves 1, F moves 2
...

Eventually in cycle:
    S →    (moving 1)
    F → → (moving 2)
    
F catches S from behind!
```

## Complexity

- **Time**: O(n)
- **Space**: O(1) - Only two pointers
