# 36. Implement Stack using Vec
**Difficulty**: Medium  
**Topics**: Stack, Design

## Problem Description

Implement a stack using a Vec (dynamic array) that supports the following operations:

- `push(x)` -- Push element x onto stack.
- `pop()` -- Removes the element on top of the stack and returns it.
- `top()` -- Get the top element.
- `is_empty()` -- Return whether the stack is empty.

## Examples

### Example 1:
```
Input:
["MyStack", "push", "push", "top", "pop", "is_empty"]
[[], [1], [2], [], [], []]

Output: [null, null, null, 2, 2, false]

Explanation:
MyStack myStack = new MyStack();
myStack.push(1);
myStack.push(2);
myStack.top();    // returns 2
myStack.pop();    // returns 2
myStack.is_empty(); // returns false
```

## Constraints

- `1 <= x <= 9`
- At most `100` calls will be made to `push`, `pop`, `top`, and `is_empty`.
- All the calls to `pop` and `top` are valid.

## Hints

<details>
<summary>Hint 1</summary>
A Vec in Rust already provides the exact behavior needed for a stack.
</details>

<details>
<summary>Hint 2</summary>
Use push() to add elements and pop() to remove from the end.
</details>

<details>
<summary>Hint 3</summary>
Use last() to peek at the top element without removing it.
</details>

## Function Signature

```rust
struct MyStack {
    data: Vec<i32>,
}

impl MyStack {
    fn new() -> Self {
        
    }
    
    fn push(&mut self, x: i32) {
        
    }
    
    fn pop(&mut self) -> i32 {
        
    }
    
    fn top(&self) -> i32 {
        
    }
    
    fn is_empty(&self) -> bool {
        
    }
}
```
