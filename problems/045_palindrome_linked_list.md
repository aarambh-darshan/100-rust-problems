# 45. Palindrome Linked List
**Difficulty**: Medium  
**Topics**: Linked List, Two Pointers, Stack

## Problem Description

Given the `head` of a singly linked list, return `true` if it is a palindrome or `false` otherwise.

## Examples

### Example 1:
```
Input: head = [1,2,2,1]
Output: true
```

### Example 2:
```
Input: head = [1,2]
Output: false
```

## Constraints

- The number of nodes in the list is in the range `[1, 10^5]`.
- `0 <= Node.val <= 9`

## Hints

<details>
<summary>Hint 1</summary>
One approach: Copy values to an array, then check if it's a palindrome.
</details>

<details>
<summary>Hint 2</summary>
For O(1) space: Find the middle, reverse the second half, then compare both halves.
</details>

<details>
<summary>Hint 3</summary>
Use slow/fast pointers to find the middle, then reverse in-place starting from the middle.
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
    pub fn is_palindrome(head: Option<Box<ListNode>>) -> bool {
        
    }
}
```
