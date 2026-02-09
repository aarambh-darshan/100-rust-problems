# 9. Find Maximum
**Difficulty**: Easy  
**Topics**: Arrays

## Problem Description

Given an array of integers `nums`, return the maximum element in the array.

## Examples

### Example 1:
```
Input: nums = [1, 5, 3, 9, 2]
Output: 9
```

### Example 2:
```
Input: nums = [-1, -5, -3]
Output: -1
```

### Example 3:
```
Input: nums = [42]
Output: 42
```

## Constraints

- `1 <= nums.len() <= 10^4`
- `-10^4 <= nums[i] <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
Initialize max with the first element, then compare with each subsequent element.
</details>

<details>
<summary>Hint 2</summary>
In Rust, you can use iter().max() but remember it returns an Option.
</details>

<details>
<summary>Hint 3</summary>
Use iter().max().unwrap() or iter().max().copied() to get the actual value.
</details>

## Function Signature

```rust
impl Solution {
    pub fn find_max(nums: Vec<i32>) -> i32 {
        
    }
}
```
