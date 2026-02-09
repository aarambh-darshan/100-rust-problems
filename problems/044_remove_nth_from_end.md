# 44. Remove Nth Node From End of List
**Difficulty**: Medium  
**Topics**: Linked List, Two Pointers

## Problem Description

Given the `head` of a linked list, remove the `n-th` node from the end of the list and return its head.

## Examples

### Example 1:
```
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```

### Example 2:
```
Input: head = [1], n = 1
Output: []
```

### Example 3:
```
Input: head = [1,2], n = 1
Output: [1]
```

## Constraints

- The number of nodes in the list is `sz`.
- `1 <= sz <= 30`
- `0 <= Node.val <= 100`
- `1 <= n <= sz`

## Hints

<details>
<summary>Hint 1</summary>
Use two pointers with a gap of n nodes between them.
</details>

<details>
<summary>Hint 2</summary>
Move the first pointer n steps ahead, then move both pointers until the first reaches the end.
</details>

<details>
<summary>Hint 3</summary>
The second pointer will be just before the node to remove. Handle the edge case of removing the head.
</details>

## Function Signature

```rust
// Definition for singly-linked list.
#[derive(PartialEq, Eq, Clone, Debug)]
pub struct ListNode {
    pub val: i32,
    pub next: Option<Box<ListNode>>
}

impl Solution {
    pub fn remove_nth_from_end(head: Option<Box<ListNode>>, n: i32) -> Option<Box<ListNode>> {
        
    }
}
```
