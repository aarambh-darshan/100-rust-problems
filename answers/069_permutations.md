# Solution: Permutations
```rust
impl Solution {
    pub fn permute(nums: Vec<i32>) -> Vec<Vec<i32>> {
        let mut result = Vec::new();
        Self::backtrack(&nums, &mut vec![], &mut vec![false; nums.len()], &mut result);
        result
    }
    fn backtrack(nums: &[i32], curr: &mut Vec<i32>, used: &mut [bool], result: &mut Vec<Vec<i32>>) {
        if curr.len() == nums.len() { result.push(curr.clone()); return; }
        for i in 0..nums.len() {
            if used[i] { continue; }
            used[i] = true; curr.push(nums[i]);
            Self::backtrack(nums, curr, used, result);
            curr.pop(); used[i] = false;
        }
    }
}
```
**Time**: O(n!), **Space**: O(n)
