# Solution: LRU Cache
```rust
use std::collections::HashMap;
struct LRUCache { cap: usize, map: HashMap<i32, (i32, usize)>, time: usize }
impl LRUCache {
    fn new(capacity: i32) -> Self { LRUCache { cap: capacity as usize, map: HashMap::new(), time: 0 } }
    fn get(&mut self, key: i32) -> i32 {
        self.time += 1;
        match self.map.get_mut(&key) {
            Some((val, t)) => { *t = self.time; *val }
            None => -1
        }
    }
    fn put(&mut self, key: i32, value: i32) {
        self.time += 1;
        if self.map.contains_key(&key) { self.map.get_mut(&key).map(|(v, t)| { *v = value; *t = self.time; }); return; }
        if self.map.len() >= self.cap {
            let lru_key = *self.map.iter().min_by_key(|(_, (_, t))| t).unwrap().0;
            self.map.remove(&lru_key);
        }
        self.map.insert(key, (value, self.time));
    }
}
```
**Time**: O(n) eviction (use linked list for O(1)), **Space**: O(capacity)
