# Solution: Alien Dictionary
```rust
use std::collections::{HashMap, HashSet, VecDeque};
impl Solution {
    pub fn alien_order(words: Vec<String>) -> String {
        let mut graph: HashMap<char, HashSet<char>> = HashMap::new();
        let mut indegree: HashMap<char, i32> = HashMap::new();
        for w in &words { for c in w.chars() { indegree.entry(c).or_insert(0); } }
        for i in 0..words.len()-1 {
            let (w1, w2) = (&words[i], &words[i+1]);
            if w1.len() > w2.len() && w1.starts_with(w2) { return String::new(); }
            for (c1, c2) in w1.chars().zip(w2.chars()) {
                if c1 != c2 {
                    if graph.entry(c1).or_default().insert(c2) { *indegree.entry(c2).or_insert(0) += 1; }
                    break;
                }
            }
        }
        let mut queue: VecDeque<_> = indegree.iter().filter(|&(_, &d)| d == 0).map(|(&c, _)| c).collect();
        let mut result = String::new();
        while let Some(c) = queue.pop_front() {
            result.push(c);
            for &n in graph.get(&c).unwrap_or(&HashSet::new()) {
                *indegree.get_mut(&n).unwrap() -= 1;
                if indegree[&n] == 0 { queue.push_back(n); }
            }
        }
        if result.len() == indegree.len() { result } else { String::new() }
    }
}
```
**Time**: O(C), **Space**: O(1)
