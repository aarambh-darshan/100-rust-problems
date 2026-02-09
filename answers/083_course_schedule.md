# Solution: Course Schedule
```rust
use std::collections::VecDeque;
impl Solution {
    pub fn can_finish(num_courses: i32, prerequisites: Vec<Vec<i32>>) -> bool {
        let n = num_courses as usize;
        let mut graph = vec![vec![]; n];
        let mut indegree = vec![0; n];
        for p in prerequisites { graph[p[1] as usize].push(p[0] as usize); indegree[p[0] as usize] += 1; }
        let mut queue: VecDeque<_> = (0..n).filter(|&i| indegree[i] == 0).collect();
        let mut count = 0;
        while let Some(u) = queue.pop_front() {
            count += 1;
            for &v in &graph[u] { indegree[v] -= 1; if indegree[v] == 0 { queue.push_back(v); } }
        }
        count == n
    }
}
```
**Time**: O(V+E), **Space**: O(V+E)
