# Solution: Middle of Linked List

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

fn middle_node(head: Option<Box<ListNode>>) -> Option<Box<ListNode>> {
    let mut slow = &head;
    let mut fast = &head;
    
    while fast.is_some() && fast.as_ref().unwrap().next.is_some() {
        slow = &slow.as_ref().unwrap().next;
        fast = &fast.as_ref().unwrap().next.as_ref().unwrap().next;
    }
    
    slow.clone()
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

fn main() {
    // Odd length
    let list1 = create_list(&[1, 2, 3, 4, 5]);
    let mid1 = middle_node(list1);
    println!("[1,2,3,4,5] → middle = {}", mid1.as_ref().unwrap().val);
    
    // Even length
    let list2 = create_list(&[1, 2, 3, 4, 5, 6]);
    let mid2 = middle_node(list2);
    println!("[1,2,3,4,5,6] → middle = {}", mid2.as_ref().unwrap().val);
}
```

**Output:**
```
[1,2,3,4,5] → middle = 3
[1,2,3,4,5,6] → middle = 4
```

## How It Works

### Two-Pointer Technique

- **Slow**: Moves 1 step
- **Fast**: Moves 2 steps

When fast reaches end, slow is at middle!

```
[1, 2, 3, 4, 5]
 S
 F

[1, 2, 3, 4, 5]
    S
       F

[1, 2, 3, 4, 5]
       S
             F (at end)

Slow at 3 = MIDDLE!
```

### For Even Length

```
[1, 2, 3, 4, 5, 6]
 S
 F

[1, 2, 3, 4, 5, 6]
    S
       F

[1, 2, 3, 4, 5, 6]
       S
             F

[1, 2, 3, 4, 5, 6]
          S
                F (past end)

Slow at 4 = second middle
```

## Complexity

- **Time**: O(n) - One pass
- **Space**: O(1) - Two pointers
