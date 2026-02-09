# 43. Middle of the Linked List
**Difficulty**: Medium  
**Topics**: Linked List, Two Pointers

## Problem Description

Given the `head` of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the **second middle** node.

## Examples

### Example 1:
```
Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node of the list is node 3.
```

### Example 2:
```
Input: head = [1,2,3,4,5,6]
Output: [4,5,6]
Explanation: Since the list has two middle nodes with values 3 and 4, we return the second one.
```

## Constraints

- The number of nodes in the list is in the range `[1, 100]`.
- `1 <= Node.val <= 100`

## Hints

<details>
<summary>Hint 1</summary>
Use the slow and fast pointer technique.
</details>

<details>
<summary>Hint 2</summary>
Slow pointer moves one step, fast pointer moves two steps.
</details>

<details>
<summary>Hint 3</summary>
When fast reaches the end, slow is at the middle.
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
    pub fn middle_node(head: Option<Box<ListNode>>) -> Option<Box<ListNode>> {
        
    }
}
```
