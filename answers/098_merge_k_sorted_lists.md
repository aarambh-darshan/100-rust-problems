# Solution: Merge K Sorted Lists
```rust
use std::collections::BinaryHeap;
use std::cmp::Reverse;
impl Solution {
    pub fn merge_k_lists(lists: Vec<Option<Box<ListNode>>>) -> Option<Box<ListNode>> {
        let mut heap: BinaryHeap<Reverse<(i32, usize)>> = BinaryHeap::new();
        let mut lists: Vec<_> = lists.into_iter().collect();
        for (i, list) in lists.iter().enumerate() {
            if let Some(node) = list { heap.push(Reverse((node.val, i))); }
        }
        let mut dummy = Box::new(ListNode::new(0));
        let mut tail = &mut dummy;
        while let Some(Reverse((val, i))) = heap.pop() {
            tail.next = Some(Box::new(ListNode::new(val)));
            tail = tail.next.as_mut().unwrap();
            lists[i] = lists[i].take().unwrap().next;
            if let Some(node) = &lists[i] { heap.push(Reverse((node.val, i))); }
        }
        dummy.next
    }
}
```
**Time**: O(N log k), **Space**: O(k)
