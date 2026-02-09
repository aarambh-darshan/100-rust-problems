# 19. Merge Two Sorted Arrays
**Difficulty**: Easy  
**Topics**: Arrays, Two Pointers, Sorting

## Problem Description

You are given two integer arrays `nums1` and `nums2`, sorted in **non-decreasing order**.

Merge `nums1` and `nums2` into a single array sorted in **non-decreasing order**.

Return the merged sorted array.

## Examples

### Example 1:
```
Input: nums1 = [1,2,3], nums2 = [2,5,6]
Output: [1,2,2,3,5,6]
```

### Example 2:
```
Input: nums1 = [1], nums2 = []
Output: [1]
```

### Example 3:
```
Input: nums1 = [], nums2 = [1]
Output: [1]
```

## Constraints

- `0 <= nums1.len(), nums2.len() <= 200`
- `-10^9 <= nums1[i], nums2[i] <= 10^9`
- Both arrays are sorted in non-decreasing order.

## Hints

<details>
<summary>Hint 1</summary>
Use two pointers, one for each array, starting from the beginning.
</details>

<details>
<summary>Hint 2</summary>
Compare elements at both pointers, add the smaller one to the result, and advance that pointer.
</details>

<details>
<summary>Hint 3</summary>
After one array is exhausted, append the remaining elements from the other array.
</details>

## Function Signature

```rust
impl Solution {
    pub fn merge(nums1: Vec<i32>, nums2: Vec<i32>) -> Vec<i32> {
        
    }
}
```
