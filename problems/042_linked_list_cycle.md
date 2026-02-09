# 42. Linked List Cycle
**Difficulty**: Medium  
**Topics**: Linked List, Two Pointers

## Problem Description

Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer.

Return `true` if there is a cycle in the linked list. Otherwise, return `false`.

## Examples

### Example 1:
```
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
```

### Example 2:
```
Input: head = [1,2], pos = 0
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 0th node.
```

### Example 3:
```
Input: head = [1], pos = -1
Output: false
Explanation: There is no cycle in the linked list.
```

## Constraints

- The number of nodes in the list is in the range `[0, 10^4]`.
- `-10^5 <= Node.val <= 10^5`
- `pos` is `-1` or a valid index in the linked-list.

## Hints

<details>
<summary>Hint 1</summary>
Use Floyd's Cycle Detection algorithm (tortoise and hare).
</details>

<details>
<summary>Hint 2</summary>
Use two pointers: slow moves one step at a time, fast moves two steps at a time.
</details>

<details>
<summary>Hint 3</summary>
If there's a cycle, the fast pointer will eventually meet the slow pointer.
</details>

## Function Signature

```rust
// Note: Cycle detection with Rust's ownership is tricky.
// This is typically solved using raw pointers or Rc<RefCell<>>.

use std::rc::Rc;
use std::cell::RefCell;

#[derive(Debug)]
pub struct ListNode {
    pub val: i32,
    pub next: Option<Rc<RefCell<ListNode>>>
}

impl Solution {
    pub fn has_cycle(head: Option<Rc<RefCell<ListNode>>>) -> bool {
        
    }
}
```
