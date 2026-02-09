# 69. Permutations
**Difficulty**: Medium  
**Topics**: Arrays, Backtracking

## Problem Description

Given an array `nums` of distinct integers, return all the possible permutations. You can return the answer in **any order**.

## Examples

### Example 1:
```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

### Example 2:
```
Input: nums = [0,1]
Output: [[0,1],[1,0]]
```

### Example 3:
```
Input: nums = [1]
Output: [[1]]
```

## Constraints

- `1 <= nums.len() <= 6`
- `-10 <= nums[i] <= 10`
- All the integers of `nums` are **unique**.

## Hints

<details>
<summary>Hint 1</summary>
Use backtracking: at each step, try placing each unused number at the current position.
</details>

<details>
<summary>Hint 2</summary>
Keep track of which elements have been used in the current permutation.
</details>

<details>
<summary>Hint 3</summary>
When the permutation length equals the input length, add it to the result.
</details>

## Function Signature

```rust
impl Solution {
    pub fn permute(nums: Vec<i32>) -> Vec<Vec<i32>> {
        
    }
}
```
