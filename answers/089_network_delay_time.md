# Solution: Network Delay Time
```rust
use std::collections::BinaryHeap;
use std::cmp::Reverse;
impl Solution {
    pub fn network_delay_time(times: Vec<Vec<i32>>, n: i32, k: i32) -> i32 {
        let mut graph = vec![vec![]; n as usize + 1];
        for t in times { graph[t[0] as usize].push((t[1] as usize, t[2])); }
        let mut dist = vec![i32::MAX; n as usize + 1];
        dist[k as usize] = 0;
        let mut heap = BinaryHeap::from([Reverse((0, k as usize))]);
        while let Some(Reverse((d, u))) = heap.pop() {
            if d > dist[u] { continue; }
            for &(v, w) in &graph[u] {
                if dist[u] + w < dist[v] { dist[v] = dist[u] + w; heap.push(Reverse((dist[v], v))); }
            }
        }
        let result = dist[1..].iter().max().unwrap();
        if *result == i32::MAX { -1 } else { *result }
    }
}
```
**Time**: O(E log V), **Space**: O(V + E)
