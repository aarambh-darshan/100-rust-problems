# 41. Merge Two Sorted Lists
**Difficulty**: Medium  
**Topics**: Linked List, Recursion

## Problem Description

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

## Examples

### Example 1:
```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

### Example 2:
```
Input: list1 = [], list2 = []
Output: []
```

### Example 3:
```
Input: list1 = [], list2 = [0]
Output: [0]
```

## Constraints

- The number of nodes in both lists is in the range `[0, 50]`.
- `-100 <= Node.val <= 100`
- Both `list1` and `list2` are sorted in non-decreasing order.

## Hints

<details>
<summary>Hint 1</summary>
Use a dummy head node to simplify the code - it helps avoid edge cases for the first node.
</details>

<details>
<summary>Hint 2</summary>
Compare the values at the heads of both lists, take the smaller one, and advance that pointer.
</details>

<details>
<summary>Hint 3</summary>
When one list is exhausted, append the remaining nodes of the other list.
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
    pub fn merge_two_lists(
        list1: Option<Box<ListNode>>,
        list2: Option<Box<ListNode>>
    ) -> Option<Box<ListNode>> {
        
    }
}
```
