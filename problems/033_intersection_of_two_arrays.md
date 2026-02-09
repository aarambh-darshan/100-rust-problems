# 33. Intersection of Two Arrays
**Difficulty**: Easy  
**Topics**: Arrays, HashSet, Binary Search

## Problem Description

Given two integer arrays `nums1` and `nums2`, return an array of their intersection. Each element in the result must be **unique** and you may return the result in **any order**.

## Examples

### Example 1:
```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]
```

### Example 2:
```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
Explanation: [4,9] is also accepted.
```

## Constraints

- `1 <= nums1.len(), nums2.len() <= 1000`
- `0 <= nums1[i], nums2[i] <= 1000`

## Hints

<details>
<summary>Hint 1</summary>
Convert one of the arrays to a HashSet for O(1) lookups.
</details>

<details>
<summary>Hint 2</summary>
Iterate through the other array and check if each element exists in the set.
</details>

<details>
<summary>Hint 3</summary>
Use another HashSet for the result to ensure uniqueness, or use set intersection.
</details>

## Function Signature

```rust
impl Solution {
    pub fn intersection(nums1: Vec<i32>, nums2: Vec<i32>) -> Vec<i32> {
        
    }
}
```
