# 82. Clone Graph
**Difficulty**: Hard  
**Topics**: Hash Table, DFS, BFS, Graph

## Problem Description

Given a reference of a node in a **connected** undirected graph, return a **deep copy** (clone) of the graph.

Each node in the graph contains a value (`int`) and a list (`Vec<Node>`) of its neighbors.

## Examples

### Example 1:
```
Input: adjList = [[2,4],[1,3],[2,4],[1,3]]
Output: [[2,4],[1,3],[2,4],[1,3]]
Explanation: There are 4 nodes in the graph.
- Node 1's neighbors are [2, 4]
- Node 2's neighbors are [1, 3]
- Node 3's neighbors are [2, 4]
- Node 4's neighbors are [1, 3]
```

### Example 2:
```
Input: adjList = [[]]
Output: [[]]
Explanation: The graph contains 1 node with no neighbors.
```

### Example 3:
```
Input: adjList = []
Output: []
Explanation: The graph is empty.
```

## Constraints

- The number of nodes in the graph is in the range `[0, 100]`.
- `1 <= Node.val <= 100`
- `Node.val` is unique for each node.
- There are no repeated edges and no self-loops in the graph.
- The Graph is connected and all nodes can be visited starting from the given node.

## Hints

<details>
<summary>Hint 1</summary>
Use a HashMap to map original nodes to their clones.
</details>

<details>
<summary>Hint 2</summary>
Use DFS or BFS to traverse the graph. For each node, create its clone and recursively clone its neighbors.
</details>

<details>
<summary>Hint 3</summary>
Check the HashMap before creating a new clone to avoid infinite loops and duplicate nodes.
</details>

## Function Signature

```rust
use std::rc::Rc;
use std::cell::RefCell;
use std::collections::HashMap;

#[derive(Debug, Clone)]
pub struct Node {
    pub val: i32,
    pub neighbors: Vec<Rc<RefCell<Node>>>,
}

impl Solution {
    pub fn clone_graph(node: Option<Rc<RefCell<Node>>>) -> Option<Rc<RefCell<Node>>> {
        
    }
}
```
