# 89. Network Delay Time
**Difficulty**: Hard  
**Topics**: DFS, BFS, Graph, Heap, Shortest Path

## Problem Description

You are given a network of `n` nodes, labeled from `1` to `n`. You are also given `times`, a list of travel times as directed edges `times[i] = (ui, vi, wi)`, where `ui` is the source node, `vi` is the target node, and `wi` is the time it takes for a signal to travel from source to target.

We will send a signal from a given node `k`. Return the **minimum time** it takes for all the `n` nodes to receive the signal. If it is impossible for all the `n` nodes to receive the signal, return `-1`.

## Examples

### Example 1:
```
Input: times = [[2,1,1],[2,3,1],[3,4,1]], n = 4, k = 2
Output: 2
```

### Example 2:
```
Input: times = [[1,2,1]], n = 2, k = 1
Output: 1
```

### Example 3:
```
Input: times = [[1,2,1]], n = 2, k = 2
Output: -1
```

## Constraints

- `1 <= k <= n <= 100`
- `1 <= times.len() <= 6000`
- `times[i].len() == 3`
- `1 <= ui, vi <= n`
- `ui != vi`
- `0 <= wi <= 100`
- All the pairs `(ui, vi)` are **unique**.

## Hints

<details>
<summary>Hint 1</summary>
This is a single-source shortest path problem. Use Dijkstra's algorithm.
</details>

<details>
<summary>Hint 2</summary>
Build an adjacency list. Use a min-heap to always process the node with the smallest distance.
</details>

<details>
<summary>Hint 3</summary>
The answer is the maximum distance among all nodes reachable from k.
</details>

## Function Signature

```rust
use std::collections::BinaryHeap;
use std::cmp::Reverse;

impl Solution {
    pub fn network_delay_time(times: Vec<Vec<i32>>, n: i32, k: i32) -> i32 {
        
    }
}
```
