# 71. House Robber
**Difficulty**: Hard  
**Topics**: Dynamic Programming

## Problem Description

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given an integer array `nums` representing the amount of money of each house, return the maximum amount of money you can rob tonight **without alerting the police**.

## Examples

### Example 1:
```
Input: nums = [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
```

### Example 2:
```
Input: nums = [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
Total amount you can rob = 2 + 9 + 1 = 12.
```

## Constraints

- `1 <= nums.len() <= 100`
- `0 <= nums[i] <= 400`

## Hints

<details>
<summary>Hint 1</summary>
At each house, you have two choices: rob it (add to money from 2 houses ago) or skip it (keep money from previous house).
</details>

<details>
<summary>Hint 2</summary>
Define dp[i] = max money you can rob from houses 0 to i.
</details>

<details>
<summary>Hint 3</summary>
dp[i] = max(dp[i-1], dp[i-2] + nums[i]). You only need to track the last two values.
</details>

## Function Signature

```rust
impl Solution {
    pub fn rob(nums: Vec<i32>) -> i32 {
        
    }
}
```
