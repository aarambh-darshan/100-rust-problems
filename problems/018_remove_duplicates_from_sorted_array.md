# 18. Remove Duplicates from Sorted Array
**Difficulty**: Easy  
**Topics**: Arrays, Two Pointers

## Problem Description

Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates **in-place** such that each unique element appears only once. The **relative order** of the elements should be kept the same.

Return the number of unique elements in `nums`.

## Examples

### Example 1:
```
Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2.
```

### Example 2:
```
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements being 0, 1, 2, 3, and 4.
```

## Constraints

- `1 <= nums.len() <= 3 * 10^4`
- `-100 <= nums[i] <= 100`
- `nums` is sorted in non-decreasing order.

## Hints

<details>
<summary>Hint 1</summary>
Since the array is sorted, duplicates will be adjacent to each other.
</details>

<details>
<summary>Hint 2</summary>
Use two pointers: one for the position to place the next unique element, one to scan through the array.
</details>

<details>
<summary>Hint 3</summary>
Compare each element with the previous unique element. If different, copy it to the unique position.
</details>

## Function Signature

```rust
impl Solution {
    pub fn remove_duplicates(nums: &mut Vec<i32>) -> i32 {
        
    }
}
```
