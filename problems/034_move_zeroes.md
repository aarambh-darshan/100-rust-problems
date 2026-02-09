# 34. Move Zeroes
**Difficulty**: Easy  
**Topics**: Arrays, Two Pointers

## Problem Description

Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Note** that you must do this in-place without making a copy of the array.

## Examples

### Example 1:
```
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```

### Example 2:
```
Input: nums = [0]
Output: [0]
```

## Constraints

- `1 <= nums.len() <= 10^4`
- `-2^31 <= nums[i] <= 2^31 - 1`

## Hints

<details>
<summary>Hint 1</summary>
Use two pointers: one for the position to place the next non-zero element.
</details>

<details>
<summary>Hint 2</summary>
Iterate through the array. When you find a non-zero, place it at the write pointer position.
</details>

<details>
<summary>Hint 3</summary>
After processing all elements, fill the remaining positions with zeros.
</details>

## Function Signature

```rust
impl Solution {
    pub fn move_zeroes(nums: &mut Vec<i32>) {
        
    }
}
```
