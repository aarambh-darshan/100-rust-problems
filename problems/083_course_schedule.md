# 83. Course Schedule
**Difficulty**: Hard  
**Topics**: DFS, BFS, Graph, Topological Sort

## Problem Description

There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses - 1`. You are given an array `prerequisites` where `prerequisites[i] = [ai, bi]` indicates that you **must** take course `bi` first if you want to take course `ai`.

Return `true` if you can finish all courses. Otherwise, return `false`.

## Examples

### Example 1:
```
Input: numCourses = 2, prerequisites = [[1,0]]
Output: true
Explanation: There are 2 courses to take. To take course 1 you should have finished course 0. So it is possible.
```

### Example 2:
```
Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
Output: false
Explanation: There are 2 courses to take. To take course 1 you should have finished course 0, and to take course 0 you should also have finished course 1. So it is impossible.
```

## Constraints

- `1 <= numCourses <= 2000`
- `0 <= prerequisites.len() <= 5000`
- `prerequisites[i].len() == 2`
- `0 <= ai, bi < numCourses`
- All the pairs `prerequisites[i]` are **unique**.

## Hints

<details>
<summary>Hint 1</summary>
This is a cycle detection problem in a directed graph.
</details>

<details>
<summary>Hint 2</summary>
Use Kahn's algorithm (BFS topological sort) or DFS with coloring (white/gray/black).
</details>

<details>
<summary>Hint 3</summary>
For BFS: Start with nodes having 0 in-degree. If all nodes are processed, no cycle exists.
</details>

## Function Signature

```rust
impl Solution {
    pub fn can_finish(num_courses: i32, prerequisites: Vec<Vec<i32>>) -> bool {
        
    }
}
```
