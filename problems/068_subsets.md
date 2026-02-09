# 68. Subsets
**Difficulty**: Medium  
**Topics**: Arrays, Backtracking, Bit Manipulation

## Problem Description

Given an integer array `nums` of **unique** elements, return all possible subsets (the power set).

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

## Examples

### Example 1:
```
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

### Example 2:
```
Input: nums = [0]
Output: [[],[0]]
```

## Constraints

- `1 <= nums.len() <= 10`
- `-10 <= nums[i] <= 10`
- All the numbers of `nums` are **unique**.

## Hints

<details>
<summary>Hint 1</summary>
Use backtracking: for each element, decide to include it or not.
</details>

<details>
<summary>Hint 2</summary>
Alternatively, use bit manipulation: each subset corresponds to a bitmask from 0 to 2^n - 1.
</details>

<details>
<summary>Hint 3</summary>
Iterative approach: start with [[]], for each number, add it to all existing subsets.
</details>

## Function Signature

```rust
impl Solution {
    pub fn subsets(nums: Vec<i32>) -> Vec<Vec<i32>> {
        
    }
}
```
