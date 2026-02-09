# Solution: Merge Two Sorted Lists

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

fn merge_two_lists(
    l1: Option<Box<ListNode>>,
    l2: Option<Box<ListNode>>,
) -> Option<Box<ListNode>> {
    match (l1, l2) {
        (None, None) => None,
        (Some(n), None) | (None, Some(n)) => Some(n),
        (Some(mut n1), Some(mut n2)) => {
            if n1.val <= n2.val {
                n1.next = merge_two_lists(n1.next, Some(n2));
                Some(n1)
            } else {
                n2.next = merge_two_lists(Some(n1), n2.next);
                Some(n2)
            }
        }
    }
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
    let l1 = create_list(&[1, 2, 4]);
    let l2 = create_list(&[1, 3, 4]);
    
    println!("List 1: {:?}", list_to_vec(&l1));
    println!("List 2: {:?}", list_to_vec(&l2));
    
    let merged = merge_two_lists(l1, l2);
    println!("Merged: {:?}", list_to_vec(&merged));
}
```

**Output:**
```
List 1: [1, 2, 4]
List 2: [1, 3, 4]
Merged: [1, 1, 2, 3, 4, 4]
```

## How It Works

### Recursive Merge

Compare heads of both lists, take the smaller one, and recursively merge the rest.

```
merge([1,2,4], [1,3,4]):
  1 <= 1, take 1 from L1
  → 1 → merge([2,4], [1,3,4])
        1 <= 2, take 1 from L2
        → 1 → merge([2,4], [3,4])
              2 <= 3, take 2 from L1
              → 2 → merge([4], [3,4])
                    ...
```

### Visual

```
L1: 1 → 2 → 4
L2: 1 → 3 → 4

Compare 1 vs 1: take L1's 1
  1 → [merge rest]

Compare 2 vs 1: take L2's 1
  1 → 1 → [merge rest]

Compare 2 vs 3: take L1's 2
  1 → 1 → 2 → [merge rest]

...

Result: 1 → 1 → 2 → 3 → 4 → 4
```

## Complexity

- **Time**: O(n + m)
- **Space**: O(n + m) for recursion stack
