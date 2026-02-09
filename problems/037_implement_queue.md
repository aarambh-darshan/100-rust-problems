# 37. Implement Queue using Vec
**Difficulty**: Medium  
**Topics**: Queue, Design

## Problem Description

Implement a queue using a Vec (dynamic array) that supports the following operations:

- `push(x)` -- Push element x to the back of queue.
- `pop()` -- Removes the element from the front of queue and returns it.
- `peek()` -- Get the front element.
- `is_empty()` -- Return whether the queue is empty.

## Examples

### Example 1:
```
Input:
["MyQueue", "push", "push", "peek", "pop", "is_empty"]
[[], [1], [2], [], [], []]

Output: [null, null, null, 1, 1, false]

Explanation:
MyQueue myQueue = new MyQueue();
myQueue.push(1);
myQueue.push(2);
myQueue.peek();   // returns 1
myQueue.pop();    // returns 1
myQueue.is_empty(); // returns false
```

## Constraints

- `1 <= x <= 9`
- At most `100` calls will be made to `push`, `pop`, `peek`, and `is_empty`.
- All the calls to `pop` and `peek` are valid.

## Hints

<details>
<summary>Hint 1</summary>
Consider using VecDeque from std::collections for efficient front and back operations.
</details>

<details>
<summary>Hint 2</summary>
With a regular Vec, removing from the front is O(n). Consider alternative approaches.
</details>

<details>
<summary>Hint 3</summary>
You can use two stacks (Vecs) to implement an efficient queue - one for pushing, one for popping.
</details>

## Function Signature

```rust
use std::collections::VecDeque;

struct MyQueue {
    data: VecDeque<i32>,
}

impl MyQueue {
    fn new() -> Self {
        
    }
    
    fn push(&mut self, x: i32) {
        
    }
    
    fn pop(&mut self) -> i32 {
        
    }
    
    fn peek(&self) -> i32 {
        
    }
    
    fn is_empty(&self) -> bool {
        
    }
}
```
