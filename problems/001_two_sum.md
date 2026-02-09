# 1. Two Sum
**Difficulty**: Easy  
**Topics**: Arrays, HashMap

## Problem Description

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have **exactly one solution**, and you may not use the same element twice.

You can return the answer in any order.

## Examples

### Example 1:
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

### Example 2:
```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

### Example 3:
```
Input: nums = [3,3], target = 6
Output: [0,1]
```

## Constraints

- `2 <= nums.len() <= 10^4`
- `-10^9 <= nums[i] <= 10^9`
- `-10^9 <= target <= 10^9`
- Only one valid answer exists.

## Hints

<details>
<summary>Hint 1</summary>
A brute force approach would be to check every pair of numbers. Can you think of a way to do this?
</details>

<details>
<summary>Hint 2</summary>
For each number, you need to find if its complement (target - num) exists in the array.
</details>

<details>
<summary>Hint 3</summary>
Use a HashMap to store numbers you've seen. For each number, check if (target - num) is already in the map.
</details>

## Function Signature

```rust
impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        
    }
}
```
