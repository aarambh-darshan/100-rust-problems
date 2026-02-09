# 24. Remove Element
**Difficulty**: Easy  
**Topics**: Arrays, Two Pointers

## Problem Description

Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` **in-place**. The order of the elements may be changed. Then return the number of elements in `nums` which are not equal to `val`.

## Examples

### Example 1:
```
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2,_,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 2.
```

### Example 2:
```
Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5, nums = [0,1,4,0,3,_,_,_]
Explanation: Your function should return k = 5, with the first five elements containing 0, 0, 1, 3, and 4.
```

## Constraints

- `0 <= nums.len() <= 100`
- `0 <= nums[i] <= 50`
- `0 <= val <= 100`

## Hints

<details>
<summary>Hint 1</summary>
Use two pointers: one to track the position for the next valid element, one to scan through the array.
</details>

<details>
<summary>Hint 2</summary>
When you find an element that's not val, copy it to the position tracked by the first pointer.
</details>

<details>
<summary>Hint 3</summary>
In Rust, you could also use retain(): nums.retain(|&x| x != val)
</details>

## Function Signature

```rust
impl Solution {
    pub fn remove_element(nums: &mut Vec<i32>, val: i32) -> i32 {
        
    }
}
```
