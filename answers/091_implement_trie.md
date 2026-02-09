# Solution: Implement Trie
```rust
use std::collections::HashMap;
#[derive(Default)]
struct TrieNode { children: HashMap<char, TrieNode>, is_end: bool }
struct Trie { root: TrieNode }
impl Trie {
    fn new() -> Self { Trie { root: TrieNode::default() } }
    fn insert(&mut self, word: String) {
        let mut node = &mut self.root;
        for c in word.chars() { node = node.children.entry(c).or_default(); }
        node.is_end = true;
    }
    fn search(&self, word: String) -> bool {
        let mut node = &self.root;
        for c in word.chars() { match node.children.get(&c) { Some(n) => node = n, None => return false } }
        node.is_end
    }
    fn starts_with(&self, prefix: String) -> bool {
        let mut node = &self.root;
        for c in prefix.chars() { match node.children.get(&c) { Some(n) => node = n, None => return false } }
        true
    }
}
```
**Time**: O(L) per operation, **Space**: O(N*L)
