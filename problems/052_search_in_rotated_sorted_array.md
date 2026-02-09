# 52. Search in Rotated Sorted Array
**Difficulty**: Medium  
**Topics**: Arrays, Binary Search

## Problem Description

There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.len()`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (0-indexed).

Given the array `nums` **after** the possible rotation and an integer `target`, return the index of `target` if it is in `nums`, or `-1` if it is not in `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

## Examples

### Example 1:
```
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

### Example 2:
```
Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```

### Example 3:
```
Input: nums = [1], target = 0
Output: -1
```

## Constraints

- `1 <= nums.len() <= 5000`
- `-10^4 <= nums[i] <= 10^4`
- All values of `nums` are unique.
- `nums` is an ascending array that is possibly rotated.
- `-10^4 <= target <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
One half of the array is always sorted. Determine which half by comparing mid with left/right.
</details>

<details>
<summary>Hint 2</summary>
If the left half is sorted and target is in that range, search left. Otherwise, search right.
</details>

<details>
<summary>Hint 3</summary>
Check: if nums[left] <= nums[mid], left half is sorted. Otherwise, right half is sorted.
</details>

## Function Signature

```rust
impl Solution {
    pub fn search(nums: Vec<i32>, target: i32) -> i32 {
        
    }
}
```
