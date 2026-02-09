# 28. Single Number
**Difficulty**: Easy  
**Topics**: Arrays, Bit Manipulation

## Problem Description

Given a **non-empty** array of integers `nums`, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

## Examples

### Example 1:
```
Input: nums = [2,2,1]
Output: 1
```

### Example 2:
```
Input: nums = [4,1,2,1,2]
Output: 4
```

### Example 3:
```
Input: nums = [1]
Output: 1
```

## Constraints

- `1 <= nums.len() <= 3 * 10^4`
- `-3 * 10^4 <= nums[i] <= 3 * 10^4`
- Each element in the array appears twice except for one element which appears only once.

## Hints

<details>
<summary>Hint 1</summary>
XOR has useful properties: a ^ a = 0 and a ^ 0 = a.
</details>

<details>
<summary>Hint 2</summary>
XOR is commutative and associative, so the order doesn't matter.
</details>

<details>
<summary>Hint 3</summary>
XOR all numbers together. Pairs will cancel out (a ^ a = 0), leaving only the single number.
</details>

## Function Signature

```rust
impl Solution {
    pub fn single_number(nums: Vec<i32>) -> i32 {
        
    }
}
```
