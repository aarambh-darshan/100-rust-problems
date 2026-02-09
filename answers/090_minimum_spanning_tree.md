# Solution: Minimum Spanning Tree (Kruskal's)
```rust
impl Solution {
    pub fn min_spanning_tree(n: i32, mut edges: Vec<Vec<i32>>) -> i32 {
        edges.sort_by_key(|e| e[2]);
        let mut parent: Vec<usize> = (0..n as usize).collect();
        let mut rank = vec![0; n as usize];
        fn find(parent: &mut [usize], x: usize) -> usize {
            if parent[x] != x { parent[x] = find(parent, parent[x]); }
            parent[x]
        }
        fn union(parent: &mut [usize], rank: &mut [i32], x: usize, y: usize) -> bool {
            let (px, py) = (find(parent, x), find(parent, y));
            if px == py { return false; }
            if rank[px] < rank[py] { parent[px] = py; }
            else if rank[px] > rank[py] { parent[py] = px; }
            else { parent[py] = px; rank[px] += 1; }
            true
        }
        let (mut cost, mut count) = (0, 0);
        for e in edges {
            if union(&mut parent, &mut rank, e[0] as usize, e[1] as usize) {
                cost += e[2]; count += 1;
                if count == n - 1 { return cost; }
            }
        }
        -1
    }
}
```
**Time**: O(E log E), **Space**: O(V)
