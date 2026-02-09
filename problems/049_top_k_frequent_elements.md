# 49. Top K Frequent Elements
**Difficulty**: Medium  
**Topics**: Arrays, HashMap, Heap, Bucket Sort

## Problem Description

Given an integer array `nums` and an integer `k`, return the `k` most frequent elements. You may return the answer in **any order**.

## Examples

### Example 1:
```
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

### Example 2:
```
Input: nums = [1], k = 1
Output: [1]
```

## Constraints

- `1 <= nums.len() <= 10^5`
- `-10^4 <= nums[i] <= 10^4`
- `k` is in the range `[1, the number of unique elements in the array]`.
- It is guaranteed that the answer is unique.

## Hints

<details>
<summary>Hint 1</summary>
First, count the frequency of each element using a HashMap.
</details>

<details>
<summary>Hint 2</summary>
Use a min-heap of size k to keep the k most frequent elements.
</details>

<details>
<summary>Hint 3</summary>
Alternative: Use bucket sort - create buckets indexed by frequency, then collect from highest frequency.
</details>

## Function Signature

```rust
use std::collections::HashMap;

impl Solution {
    pub fn top_k_frequent(nums: Vec<i32>, k: i32) -> Vec<i32> {
        
    }
}
```
