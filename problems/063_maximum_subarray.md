# 63. Maximum Subarray
**Difficulty**: Medium  
**Topics**: Arrays, Dynamic Programming, Divide and Conquer

## Problem Description

Given an integer array `nums`, find the subarray with the largest sum, and return its sum.

## Examples

### Example 1:
```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.
```

### Example 2:
```
Input: nums = [1]
Output: 1
```

### Example 3:
```
Input: nums = [5,4,-1,7,8]
Output: 23
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.
```

## Constraints

- `1 <= nums.len() <= 10^5`
- `-10^4 <= nums[i] <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
Use Kadane's algorithm: track the maximum sum ending at each position.
</details>

<details>
<summary>Hint 2</summary>
At each position, decide: extend the previous subarray or start a new one here.
</details>

<details>
<summary>Hint 3</summary>
current_sum = max(nums[i], current_sum + nums[i]). Track the maximum seen.
</details>

## Function Signature

```rust
impl Solution {
    pub fn max_sub_array(nums: Vec<i32>) -> i32 {
        
    }
}
```
