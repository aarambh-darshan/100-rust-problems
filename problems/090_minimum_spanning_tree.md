# 90. Minimum Spanning Tree (Kruskal's Algorithm)
**Difficulty**: Hard  
**Topics**: Graph, Union Find, MST

## Problem Description

You are given a weighted undirected graph with `n` nodes labeled from `0` to `n - 1`. The graph is represented by an edge list `edges` where `edges[i] = [ui, vi, weight]` denotes an edge between nodes `ui` and `vi` with weight `weight`.

Return the **minimum cost** to connect all nodes in the graph. If it is impossible to connect all nodes, return `-1`.

## Examples

### Example 1:
```
Input: n = 4, edges = [[0,1,1],[1,2,2],[2,3,3],[0,3,4],[1,3,5]]
Output: 6
Explanation: The minimum spanning tree uses edges [0,1,1], [1,2,2], [2,3,3] with total weight 6.
```

### Example 2:
```
Input: n = 4, edges = [[0,1,1],[1,2,2]]
Output: -1
Explanation: Not all nodes can be connected.
```

## Constraints

- `1 <= n <= 1000`
- `0 <= edges.len() <= n * (n - 1) / 2`
- `edges[i].len() == 3`
- `0 <= ui, vi < n`
- `ui != vi`
- `1 <= weight <= 10^6`
- No duplicate edges.

## Hints

<details>
<summary>Hint 1</summary>
Use Kruskal's algorithm: Sort edges by weight, then greedily add edges that don't create a cycle.
</details>

<details>
<summary>Hint 2</summary>
Use Union-Find to efficiently detect if adding an edge creates a cycle.
</details>

<details>
<summary>Hint 3</summary>
Stop when you've added n-1 edges. If you can't add n-1 edges, the graph isn't connected.
</details>

## Function Signature

```rust
impl Solution {
    pub fn min_spanning_tree(n: i32, edges: Vec<Vec<i32>>) -> i32 {
        
    }
}
```
