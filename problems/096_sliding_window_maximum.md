# 96. Sliding Window Maximum
**Difficulty**: Hard  
**Topics**: Array, Queue, Sliding Window, Heap, Monotonic Queue

## Problem Description

You are given an array of integers `nums`, and there is a sliding window of size `k` which is moving from the very left of the array to the very right. You can only see the `k` numbers in the window. Each time the sliding window moves right by one position.

Return the max sliding window.

## Examples

### Example 1:
```
Input: nums = [1,3,-1,-3,5,3,6,7], k = 3
Output: [3,3,5,5,6,7]
Explanation: 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

### Example 2:
```
Input: nums = [1], k = 1
Output: [1]
```

## Constraints

- `1 <= nums.len() <= 10^5`
- `-10^4 <= nums[i] <= 10^4`
- `1 <= k <= nums.len()`

## Hints

<details>
<summary>Hint 1</summary>
Use a monotonic deque (decreasing) to efficiently track the maximum in the window.
</details>

<details>
<summary>Hint 2</summary>
The front of the deque is always the maximum in the current window.
</details>

<details>
<summary>Hint 3</summary>
Remove elements from the back if they're smaller than the new element. Remove from front if outside the window.
</details>

## Function Signature

```rust
use std::collections::VecDeque;

impl Solution {
    pub fn max_sliding_window(nums: Vec<i32>, k: i32) -> Vec<i32> {
        
    }
}
```
