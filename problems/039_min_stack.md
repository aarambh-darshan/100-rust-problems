# 39. Min Stack
**Difficulty**: Medium  
**Topics**: Stack, Design

## Problem Description

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the `MinStack` class:

- `MinStack()` initializes the stack object.
- `push(val)` pushes the element val onto the stack.
- `pop()` removes the element on the top of the stack.
- `top()` gets the top element of the stack.
- `get_min()` retrieves the minimum element in the stack.

You must implement a solution with `O(1)` time complexity for each function.

## Examples

### Example 1:
```
Input:
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Output: [null,null,null,null,-3,null,0,-2]

Explanation:
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2
```

## Constraints

- `-2^31 <= val <= 2^31 - 1`
- Methods `pop`, `top`, and `getMin` operations will always be called on non-empty stacks.
- At most `3 * 10^4` calls will be made to `push`, `pop`, `top`, and `getMin`.

## Hints

<details>
<summary>Hint 1</summary>
The challenge is maintaining the minimum in O(1) when elements are popped.
</details>

<details>
<summary>Hint 2</summary>
Use two stacks: one for values and one for tracking minimums at each level.
</details>

<details>
<summary>Hint 3</summary>
Alternatively, store tuples (value, current_min) in a single stack.
</details>

## Function Signature

```rust
struct MinStack {
    stack: Vec<(i32, i32)>, // (value, min_at_this_level)
}

impl MinStack {
    fn new() -> Self {
        
    }
    
    fn push(&mut self, val: i32) {
        
    }
    
    fn pop(&mut self) {
        
    }
    
    fn top(&self) -> i32 {
        
    }
    
    fn get_min(&self) -> i32 {
        
    }
}
```
