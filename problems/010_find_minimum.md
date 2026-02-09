# 10. Find Minimum
**Difficulty**: Easy  
**Topics**: Arrays

## Problem Description

Given an array of integers `nums`, return the minimum element in the array.

## Examples

### Example 1:
```
Input: nums = [1, 5, 3, 9, 2]
Output: 1
```

### Example 2:
```
Input: nums = [-1, -5, -3]
Output: -5
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
Initialize min with the first element, then compare with each subsequent element.
</details>

<details>
<summary>Hint 2</summary>
In Rust, you can use iter().min() but remember it returns an Option.
</details>

<details>
<summary>Hint 3</summary>
Use iter().min().unwrap() or iter().min().copied() to get the actual value.
</details>

## Function Signature

```rust
impl Solution {
    pub fn find_min(nums: Vec<i32>) -> i32 {
        
    }
}
```
