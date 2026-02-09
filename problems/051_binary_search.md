# 51. Binary Search
**Difficulty**: Medium  
**Topics**: Arrays, Binary Search

## Problem Description

Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.

You must write an algorithm with `O(log n)` runtime complexity.

## Examples

### Example 1:
```
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4.
```

### Example 2:
```
Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1.
```

## Constraints

- `1 <= nums.len() <= 10^4`
- `-10^4 < nums[i], target < 10^4`
- All the integers in `nums` are unique.
- `nums` is sorted in ascending order.

## Hints

<details>
<summary>Hint 1</summary>
Use two pointers: left and right, starting at the beginning and end of the array.
</details>

<details>
<summary>Hint 2</summary>
Calculate mid = left + (right - left) / 2 to avoid overflow.
</details>

<details>
<summary>Hint 3</summary>
If nums[mid] == target, return mid. If less, search right half. If greater, search left half.
</details>

## Function Signature

```rust
impl Solution {
    pub fn search(nums: Vec<i32>, target: i32) -> i32 {
        
    }
}
```
