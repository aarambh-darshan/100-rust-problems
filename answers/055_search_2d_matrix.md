# Solution: Search 2D Matrix
```rust
impl Solution {
    pub fn search_matrix(matrix: Vec<Vec<i32>>, target: i32) -> bool {
        let (m, n) = (matrix.len(), matrix[0].len());
        let (mut left, mut right) = (0, m * n);
        while left < right {
            let mid = left + (right - left) / 2;
            let val = matrix[mid / n][mid % n];
            match val.cmp(&target) {
                std::cmp::Ordering::Equal => return true,
                std::cmp::Ordering::Less => left = mid + 1,
                std::cmp::Ordering::Greater => right = mid,
            }
        }
        false
    }
}
```
**Time**: O(log(m*n)), **Space**: O(1)
