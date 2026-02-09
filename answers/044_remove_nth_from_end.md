# Solution: Remove Nth Node From End

## Complete Runnable Code

```rust
#[derive(Debug, Clone)]
struct ListNode {
    val: i32,
    next: Option<Box<ListNode>>,
}

impl ListNode {
    fn new(val: i32) -> Self {
        ListNode { val, next: None }
    }
}

fn remove_nth_from_end(head: Option<Box<ListNode>>, n: i32) -> Option<Box<ListNode>> {
    // Count list length
    let mut len = 0;
    let mut ptr = &head;
    while let Some(node) = ptr {
        len += 1;
        ptr = &node.next;
    }
    
    // Edge case: remove first node
    if len == n as usize {
        return head.and_then(|node| node.next);
    }
    
    // Find node before the one to remove
    let mut head = head;
    let target = len - n as usize - 1;
    let mut current = &mut head;
    
    for _ in 0..target {
        current = &mut current.as_mut().unwrap().next;
    }
    
    // Remove the nth node
    let next_next = current.as_mut().unwrap().next.as_mut().unwrap().next.take();
    current.as_mut().unwrap().next = next_next;
    
    head
}

fn create_list(values: &[i32]) -> Option<Box<ListNode>> {
    let mut head = None;
    for &val in values.iter().rev() {
        let mut node = Box::new(ListNode::new(val));
        node.next = head;
        head = Some(node);
    }
    head
}

fn list_to_vec(head: &Option<Box<ListNode>>) -> Vec<i32> {
    let mut result = Vec::new();
    let mut current = head;
    while let Some(node) = current {
        result.push(node.val);
        current = &node.next;
    }
    result
}

fn main() {
    let test_cases = vec![
        (vec![1, 2, 3, 4, 5], 2),  // Remove 4
        (vec![1], 1),              // Remove only node
        (vec![1, 2], 1),           // Remove last
        (vec![1, 2], 2),           // Remove first
    ];
    
    for (values, n) in test_cases {
        let list = create_list(&values);
        let result = remove_nth_from_end(list, n);
        println!("Remove {}th from end of {:?} → {:?}", n, values, list_to_vec(&result));
    }
}
```

**Output:**
```
Remove 2th from end of [1, 2, 3, 4, 5] → [1, 2, 3, 5]
Remove 1th from end of [1] → []
Remove 1th from end of [1, 2] → [1]
Remove 2th from end of [1, 2] → [2]
```

## How It Works

### Two-Pass Approach

1. **First pass**: Count total length
2. **Calculate**: Node to remove is at position `length - n`
3. **Second pass**: Navigate to node before target, skip target

### Visual

```
Remove 2nd from end of [1,2,3,4,5]:

Length = 5
Position to remove = 5 - 2 = 3 (0-indexed)

[1, 2, 3, 4, 5]
          ↑
          Remove this (4)

Navigate to node at position 2 (value 3)
Point it to node at position 4 (value 5)

Result: [1, 2, 3, 5]
```

## Complexity

- **Time**: O(n) - Two passes
- **Space**: O(1)
