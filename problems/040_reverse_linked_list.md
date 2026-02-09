# 40. Reverse Linked List
**Difficulty**: Medium  
**Topics**: Linked List, Recursion

## Problem Description

Given the `head` of a singly linked list, reverse the list, and return the reversed list.

## Examples

### Example 1:
```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

### Example 2:
```
Input: head = [1,2]
Output: [2,1]
```

### Example 3:
```
Input: head = []
Output: []
```

## Constraints

- The number of nodes in the list is the range `[0, 5000]`.
- `-5000 <= Node.val <= 5000`

## Hints

<details>
<summary>Hint 1</summary>
Use three pointers: prev, current, and next. Initially, prev is None.
</details>

<details>
<summary>Hint 2</summary>
For each node: save next, point current to prev, move prev to current, move current to next.
</details>

<details>
<summary>Hint 3</summary>
In Rust, use Option<Box<ListNode>> and take() to handle ownership carefully.
</details>

## Function Signature

```rust
// Definition for singly-linked list.
#[derive(PartialEq, Eq, Clone, Debug)]
pub struct ListNode {
    pub val: i32,
    pub next: Option<Box<ListNode>>
}

impl ListNode {
    #[inline]
    fn new(val: i32) -> Self {
        ListNode {
            next: None,
            val
        }
    }
}

impl Solution {
    pub fn reverse_list(head: Option<Box<ListNode>>) -> Option<Box<ListNode>> {
        
    }
}
```
