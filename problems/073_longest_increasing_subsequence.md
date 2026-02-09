# 73. Longest Increasing Subsequence
**Difficulty**: Hard  
**Topics**: Arrays, Binary Search, Dynamic Programming

## Problem Description

Given an integer array `nums`, return the length of the longest **strictly increasing** subsequence.

## Examples

### Example 1:
```
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
```

### Example 2:
```
Input: nums = [0,1,0,3,2,3]
Output: 4
```

### Example 3:
```
Input: nums = [7,7,7,7,7,7,7]
Output: 1
```

## Constraints

- `1 <= nums.len() <= 2500`
- `-10^4 <= nums[i] <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
O(n²) DP: dp[i] = length of LIS ending at index i. For each j < i, if nums[j] < nums[i], dp[i] = max(dp[i], dp[j] + 1).
</details>

<details>
<summary>Hint 2</summary>
O(n log n): Maintain a sorted array. For each number, binary search to find where it would go.
</details>

<details>
<summary>Hint 3</summary>
In the O(n log n) solution, the length of the auxiliary array gives the LIS length.
</details>

## Function Signature

```rust
impl Solution {
    pub fn length_of_lis(nums: Vec<i32>) -> i32 {
        
    }
}
```
