# 75. Jump Game
**Difficulty**: Hard  
**Topics**: Arrays, Dynamic Programming, Greedy

## Problem Description

You are given an integer array `nums`. You are initially positioned at the array's **first index**, and each element in the array represents your maximum jump length at that position.

Return `true` if you can reach the last index, or `false` otherwise.

## Examples

### Example 1:
```
Input: nums = [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

### Example 2:
```
Input: nums = [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.
```

## Constraints

- `1 <= nums.len() <= 10^4`
- `0 <= nums[i] <= 10^5`

## Hints

<details>
<summary>Hint 1</summary>
Greedy approach: Track the farthest position you can reach.
</details>

<details>
<summary>Hint 2</summary>
For each index i, if i <= farthest, update farthest = max(farthest, i + nums[i]).
</details>

<details>
<summary>Hint 3</summary>
Return true if farthest >= last index.
</details>

## Function Signature

```rust
impl Solution {
    pub fn can_jump(nums: Vec<i32>) -> bool {
        
    }
}
```
