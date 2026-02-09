# Solution: Subsets
```rust
impl Solution {
    pub fn subsets(nums: Vec<i32>) -> Vec<Vec<i32>> {
        let mut result = vec![vec![]];
        for num in nums { 
            let new: Vec<_> = result.iter().map(|s| { let mut t = s.clone(); t.push(num); t }).collect();
            result.extend(new);
        }
        result
    }
}
```
**Time**: O(n * 2^n), **Space**: O(n * 2^n)
