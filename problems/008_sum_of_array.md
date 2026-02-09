# 8. Sum of Array
**Difficulty**: Easy  
**Topics**: Arrays

## Problem Description

Given an array of integers `nums`, return the sum of all elements in the array.

## Examples

### Example 1:
```
Input: nums = [1, 2, 3, 4, 5]
Output: 15
Explanation: 1 + 2 + 3 + 4 + 5 = 15
```

### Example 2:
```
Input: nums = [-1, 0, 1]
Output: 0
Explanation: -1 + 0 + 1 = 0
```

### Example 3:
```
Input: nums = [10]
Output: 10
```

## Constraints

- `1 <= nums.len() <= 10^4`
- `-10^4 <= nums[i] <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
Initialize a sum variable to 0 and iterate through the array.
</details>

<details>
<summary>Hint 2</summary>
In Rust, you can use the iter() and sum() methods for a clean solution.
</details>

<details>
<summary>Hint 3</summary>
You can also use fold() to accumulate the sum: nums.iter().fold(0, |acc, &x| acc + x)
</details>

## Function Signature

```rust
impl Solution {
    pub fn sum_array(nums: Vec<i32>) -> i32 {
        
    }
}
```
