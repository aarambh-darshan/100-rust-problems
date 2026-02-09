# 25. Search Insert Position
**Difficulty**: Easy  
**Topics**: Arrays, Binary Search

## Problem Description

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with `O(log n)` runtime complexity.

## Examples

### Example 1:
```
Input: nums = [1,3,5,6], target = 5
Output: 2
```

### Example 2:
```
Input: nums = [1,3,5,6], target = 2
Output: 1
```

### Example 3:
```
Input: nums = [1,3,5,6], target = 7
Output: 4
```

## Constraints

- `1 <= nums.len() <= 10^4`
- `-10^4 <= nums[i] <= 10^4`
- `nums` contains distinct values sorted in ascending order.
- `-10^4 <= target <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
Use binary search since the array is sorted.
</details>

<details>
<summary>Hint 2</summary>
The insert position is the index of the first element greater than or equal to target.
</details>

<details>
<summary>Hint 3</summary>
In Rust, you can use binary_search() which returns Ok(index) if found, or Err(index) for insert position.
</details>

## Function Signature

```rust
impl Solution {
    pub fn search_insert(nums: Vec<i32>, target: i32) -> i32 {
        
    }
}
```
