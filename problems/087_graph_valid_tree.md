# 87. Graph Valid Tree
**Difficulty**: Hard  
**Topics**: DFS, BFS, Union Find, Graph

## Problem Description

You have a graph of `n` nodes labeled from `0` to `n - 1`. You are given an integer `n` and a list of `edges` where `edges[i] = [ai, bi]` indicates that there is an undirected edge between nodes `ai` and `bi` in the graph.

Return `true` if the edges of the given graph make up a valid tree, and `false` otherwise.

## Examples

### Example 1:
```
Input: n = 5, edges = [[0,1],[0,2],[0,3],[1,4]]
Output: true
```

### Example 2:
```
Input: n = 5, edges = [[0,1],[1,2],[2,3],[1,3],[1,4]]
Output: false
```

## Constraints

- `1 <= n <= 2000`
- `0 <= edges.len() <= 5000`
- `edges[i].len() == 2`
- `0 <= ai, bi < n`
- `ai != bi`
- There are no self-loops or repeated edges.

## Hints

<details>
<summary>Hint 1</summary>
A valid tree must have exactly n-1 edges and be connected.
</details>

<details>
<summary>Hint 2</summary>
First check if edges.len() == n - 1. If not, it's definitely not a tree.
</details>

<details>
<summary>Hint 3</summary>
Use DFS/BFS or Union-Find to check if all nodes are connected without cycles.
</details>

## Function Signature

```rust
impl Solution {
    pub fn valid_tree(n: i32, edges: Vec<Vec<i32>>) -> bool {
        
    }
}
```
