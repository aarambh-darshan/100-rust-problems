# Solution: Combination Sum
```rust
impl Solution {
    pub fn combination_sum(candidates: Vec<i32>, target: i32) -> Vec<Vec<i32>> {
        let mut result = Vec::new();
        Self::backtrack(&candidates, target, 0, &mut vec![], &mut result);
        result
    }
    fn backtrack(cands: &[i32], remain: i32, start: usize, curr: &mut Vec<i32>, result: &mut Vec<Vec<i32>>) {
        if remain == 0 { result.push(curr.clone()); return; }
        for i in start..cands.len() {
            if cands[i] > remain { continue; }
            curr.push(cands[i]);
            Self::backtrack(cands, remain - cands[i], i, curr, result);
            curr.pop();
        }
    }
}
```
**Time**: O(N^(T/M)), **Space**: O(T/M)
