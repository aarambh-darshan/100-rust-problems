# Solution: Find Median from Data Stream
```rust
use std::collections::BinaryHeap;
use std::cmp::Reverse;
struct MedianFinder { small: BinaryHeap<i32>, large: BinaryHeap<Reverse<i32>> }
impl MedianFinder {
    fn new() -> Self { MedianFinder { small: BinaryHeap::new(), large: BinaryHeap::new() } }
    fn add_num(&mut self, num: i32) {
        self.small.push(num);
        self.large.push(Reverse(self.small.pop().unwrap()));
        if self.large.len() > self.small.len() { self.small.push(self.large.pop().unwrap().0); }
    }
    fn find_median(&self) -> f64 {
        if self.small.len() > self.large.len() { *self.small.peek().unwrap() as f64 }
        else { (*self.small.peek().unwrap() + self.large.peek().unwrap().0) as f64 / 2.0 }
    }
}
```
**Time**: O(log n) add, O(1) find, **Space**: O(n)
