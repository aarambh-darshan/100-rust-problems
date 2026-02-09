# Solution: Graph Valid Tree
```rust
impl Solution {
    pub fn valid_tree(n: i32, edges: Vec<Vec<i32>>) -> bool {
        if edges.len() != n as usize - 1 { return false; }
        let mut parent: Vec<usize> = (0..n as usize).collect();
        fn find(parent: &mut [usize], x: usize) -> usize {
            if parent[x] != x { parent[x] = find(parent, parent[x]); }
            parent[x]
        }
        for e in edges {
            let (px, py) = (find(&mut parent, e[0] as usize), find(&mut parent, e[1] as usize));
            if px == py { return false; }
            parent[px] = py;
        }
        true
    }
}
```
**Time**: O(E * α(n)), **Space**: O(n)
