# 98. Merge K Sorted Lists
**Difficulty**: Hard  
**Topics**: Linked List, Divide and Conquer, Heap, Merge Sort

## Problem Description

You are given an array of `k` linked-lists `lists`, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.

## Examples

### Example 1:
```
Input: lists = [[1,4,5],[1,3,4],[2,6]]
Output: [1,1,2,3,4,4,5,6]
Explanation: The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted list:
1->1->2->3->4->4->5->6
```

### Example 2:
```
Input: lists = []
Output: []
```

### Example 3:
```
Input: lists = [[]]
Output: []
```

## Constraints

- `k == lists.len()`
- `0 <= k <= 10^4`
- `0 <= lists[i].len() <= 500`
- `-10^4 <= lists[i][j] <= 10^4`
- `lists[i]` is sorted in ascending order.
- The sum of `lists[i].len()` won't exceed `10^4`.

## Hints

<details>
<summary>Hint 1</summary>
Use a min-heap to always get the smallest element among all list heads.
</details>

<details>
<summary>Hint 2</summary>
Alternative: Merge lists pairwise repeatedly (divide and conquer).
</details>

<details>
<summary>Hint 3</summary>
In Rust, you'll need to implement Ord for the ListNode or use a wrapper.
</details>

## Function Signature

```rust
use std::collections::BinaryHeap;
use std::cmp::{Ordering, Reverse};

#[derive(PartialEq, Eq, Clone, Debug)]
pub struct ListNode {
    pub val: i32,
    pub next: Option<Box<ListNode>>
}

impl Solution {
    pub fn merge_k_lists(lists: Vec<Option<Box<ListNode>>>) -> Option<Box<ListNode>> {
        
    }
}
```
