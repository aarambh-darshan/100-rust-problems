# 56. Sort Colors
**Difficulty**: Medium  
**Topics**: Arrays, Two Pointers, Sorting

## Problem Description

Given an array `nums` with `n` objects colored red, white, or blue, sort them **in-place** so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers `0`, `1`, and `2` to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.

## Examples

### Example 1:
```
Input: nums = [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]
```

### Example 2:
```
Input: nums = [2,0,1]
Output: [0,1,2]
```

## Constraints

- `n == nums.len()`
- `1 <= n <= 300`
- `nums[i]` is either `0`, `1`, or `2`.

## Hints

<details>
<summary>Hint 1</summary>
Count the occurrences of 0, 1, and 2, then overwrite the array.
</details>

<details>
<summary>Hint 2</summary>
For a one-pass solution, use the Dutch National Flag algorithm with three pointers.
</details>

<details>
<summary>Hint 3</summary>
Use pointers low (for 0s), mid (current), and high (for 2s). Swap elements based on the value at mid.
</details>

## Function Signature

```rust
impl Solution {
    pub fn sort_colors(nums: &mut Vec<i32>) {
        
    }
}
```
