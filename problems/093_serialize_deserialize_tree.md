# 93. Serialize and Deserialize Binary Tree
**Difficulty**: Hard  
**Topics**: String, Tree, DFS, BFS, Design

## Problem Description

Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

## Examples

### Example 1:
```
Input: root = [1,2,3,null,null,4,5]
Output: [1,2,3,null,null,4,5]
```

### Example 2:
```
Input: root = []
Output: []
```

## Constraints

- The number of nodes in the tree is in the range `[0, 10^4]`.
- `-1000 <= Node.val <= 1000`

## Hints

<details>
<summary>Hint 1</summary>
Use preorder traversal for serialization. Represent null nodes with a special marker (e.g., "null" or "#").
</details>

<details>
<summary>Hint 2</summary>
Separate values with a delimiter (e.g., comma).
</details>

<details>
<summary>Hint 3</summary>
For deserialization, use a queue or iterator to process values in order, recursively building the tree.
</details>

## Function Signature

```rust
use std::rc::Rc;
use std::cell::RefCell;

#[derive(Debug, PartialEq, Eq)]
pub struct TreeNode {
    pub val: i32,
    pub left: Option<Rc<RefCell<TreeNode>>>,
    pub right: Option<Rc<RefCell<TreeNode>>>,
}

struct Codec;

impl Codec {
    fn new() -> Self {
        
    }
    
    fn serialize(&self, root: Option<Rc<RefCell<TreeNode>>>) -> String {
        
    }
    
    fn deserialize(&self, data: String) -> Option<Rc<RefCell<TreeNode>>> {
        
    }
}
```
