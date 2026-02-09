# 46. Contains Duplicate
**Difficulty**: Medium  
**Topics**: Arrays, HashMap, Sorting

## Problem Description

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

## Examples

### Example 1:
```
Input: nums = [1,2,3,1]
Output: true
Explanation: The element 1 occurs at indices 0 and 3.
```

### Example 2:
```
Input: nums = [1,2,3,4]
Output: false
Explanation: All elements are distinct.
```

### Example 3:
```
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

## Constraints

- `1 <= nums.len() <= 10^5`
- `-10^9 <= nums[i] <= 10^9`

## Hints

<details>
<summary>Hint 1</summary>
Use a HashSet to track numbers you've seen.
</details>

<details>
<summary>Hint 2</summary>
For each number, check if it's already in the set. If yes, return true.
</details>

<details>
<summary>Hint 3</summary>
Alternative: Sort the array and check for adjacent duplicates.
</details>

## Function Signature

```rust
impl Solution {
    pub fn contains_duplicate(nums: Vec<i32>) -> bool {
        
    }
}
```
