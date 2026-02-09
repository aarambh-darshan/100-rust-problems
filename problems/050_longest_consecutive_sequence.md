# 50. Longest Consecutive Sequence
**Difficulty**: Medium  
**Topics**: Arrays, HashSet, Union Find

## Problem Description

Given an unsorted array of integers `nums`, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in `O(n)` time.

## Examples

### Example 1:
```
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
```

### Example 2:
```
Input: nums = [0,3,7,2,5,8,4,6,0,1]
Output: 9
```

## Constraints

- `0 <= nums.len() <= 10^5`
- `-10^9 <= nums[i] <= 10^9`

## Hints

<details>
<summary>Hint 1</summary>
Put all numbers in a HashSet for O(1) lookups.
</details>

<details>
<summary>Hint 2</summary>
For each number, only start counting if it's the beginning of a sequence (i.e., num-1 is not in the set).
</details>

<details>
<summary>Hint 3</summary>
From each sequence start, count consecutive numbers (num+1, num+2, ...) and track the maximum length.
</details>

## Function Signature

```rust
use std::collections::HashSet;

impl Solution {
    pub fn longest_consecutive(nums: Vec<i32>) -> i32 {
        
    }
}
```
