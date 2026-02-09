# Solution: Reverse Linked List

## Complete Runnable Code

```rust
// Definition for singly-linked list node
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

fn reverse_list(head: Option<Box<ListNode>>) -> Option<Box<ListNode>> {
    let mut prev: Option<Box<ListNode>> = None;
    let mut curr = head;
    
    while let Some(mut node) = curr {
        // Save next node
        let next = node.next.take();
        // Reverse the pointer
        node.next = prev;
        // Move prev and curr forward
        prev = Some(node);
        curr = next;
    }
    
    prev
}

// Helper: Create linked list from array
fn create_list(values: &[i32]) -> Option<Box<ListNode>> {
    let mut head = None;
    for &val in values.iter().rev() {
        let mut node = Box::new(ListNode::new(val));
        node.next = head;
        head = Some(node);
    }
    head
}

// Helper: Convert list to vector for display
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
    // Test cases
    let test_cases = vec![
        vec![1, 2, 3, 4, 5],
        vec![1, 2],
        vec![1],
        vec![],
    ];
    
    for values in test_cases {
        let list = create_list(&values);
        let reversed = reverse_list(list);
        println!("{:?} → {:?}", values, list_to_vec(&reversed));
    }
}
```

**Output:**
```
[1, 2, 3, 4, 5] → [5, 4, 3, 2, 1]
[1, 2] → [2, 1]
[1] → [1]
[] → []
```

## How It Works

### The Three-Pointer Technique

We use three pointers:
- `prev`: Node we've already reversed
- `curr`: Node we're currently processing
- `next`: Saved pointer to next node

### Step-by-Step

```
1 → 2 → 3 → NULL

Initial: prev=NULL, curr=1

Step 1: Save next=2, point 1→NULL, prev=1, curr=2
NULL ← 1   2 → 3 → NULL
       ↑   ↑
      prev curr

Step 2: Save next=3, point 2→1, prev=2, curr=3
NULL ← 1 ← 2   3 → NULL
           ↑   ↑
          prev curr

Step 3: Save next=NULL, point 3→2, prev=3, curr=NULL
NULL ← 1 ← 2 ← 3
               ↑
              prev (new head!)
```

### Visual Animation

```
Original: 1 → 2 → 3 → NULL

Step 1:   NULL ← 1   2 → 3 → NULL
                 ↑   ↑
                prev curr

Step 2:   NULL ← 1 ← 2   3 → NULL
                     ↑   ↑
                    prev curr

Step 3:   NULL ← 1 ← 2 ← 3   NULL
                         ↑   ↑
                        prev curr

Result: 3 → 2 → 1 → NULL
```

## Complexity Analysis

- **Time Complexity**: O(n) - Visit each node once
- **Space Complexity**: O(1) - Only pointer variables
