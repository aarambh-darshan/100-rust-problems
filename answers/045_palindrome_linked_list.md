# Solution: Palindrome Linked List

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

fn is_palindrome(head: Option<Box<ListNode>>) -> bool {
    // Convert to vector and compare
    let mut vals = Vec::new();
    let mut current = &head;
    
    while let Some(node) = current {
        vals.push(node.val);
        current = &node.next;
    }
    
    vals.iter().eq(vals.iter().rev())
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
    let test_cases = vec![
        vec![1, 2, 2, 1],
        vec![1, 2],
        vec![1],
        vec![1, 2, 3, 2, 1],
    ];
    
    for values in test_cases {
        let list = create_list(&values);
        let result = is_palindrome(list);
        println!("{:?} → palindrome: {}", values, result);
    }
}
```

**Output:**
```
[1, 2, 2, 1] → palindrome: true
[1, 2] → palindrome: false
[1] → palindrome: true
[1, 2, 3, 2, 1] → palindrome: true
```

## How It Works

### Simple Approach: Convert to Array

```rust
[1, 2, 2, 1] → vec![1, 2, 2, 1]

Compare: [1, 2, 2, 1] == [1, 2, 2, 1].reverse()
       = [1, 2, 2, 1] == [1, 2, 2, 1]
       = true ✓
```

### Visual

```
1 → 2 → 2 → 1

Forward:  1, 2, 2, 1
Backward: 1, 2, 2, 1
          ↕  ↕  ↕  ↕
          =  =  =  = → PALINDROME!
```

### Optimal O(1) Space Approach (Advanced)

1. Find middle using slow/fast pointers
2. Reverse second half
3. Compare both halves
4. Restore (optional)

## Complexity

- **Time**: O(n)
- **Space**: O(n) for array (O(1) for optimal approach)
