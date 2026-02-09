# 62. Product of Array Except Self
**Difficulty**: Medium  
**Topics**: Arrays, Prefix Sum

## Problem Description

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

## Examples

### Example 1:
```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```

### Example 2:
```
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```

## Constraints

- `2 <= nums.len() <= 10^5`
- `-30 <= nums[i] <= 30`
- The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.

## Hints

<details>
<summary>Hint 1</summary>
For each position, the result is the product of all elements to the left times all elements to the right.
</details>

<details>
<summary>Hint 2</summary>
First pass: Calculate prefix products (product of all elements to the left).
</details>

<details>
<summary>Hint 3</summary>
Second pass: Calculate suffix products on the fly and multiply with prefix products.
</details>

## Function Signature

```rust
impl Solution {
    pub fn product_except_self(nums: Vec<i32>) -> Vec<i32> {
        
    }
}
```
