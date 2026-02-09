# 97. Trapping Rain Water
**Difficulty**: Hard  
**Topics**: Array, Two Pointers, Dynamic Programming, Stack, Monotonic Stack

## Problem Description

Given `n` non-negative integers representing an elevation map where the width of each bar is `1`, compute how much water it can trap after raining.

## Examples

### Example 1:
```
Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The elevation map is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water are being trapped.
```

### Example 2:
```
Input: height = [4,2,0,3,2,5]
Output: 9
```

## Constraints

- `n == height.len()`
- `1 <= n <= 2 * 10^4`
- `0 <= height[i] <= 10^5`

## Hints

<details>
<summary>Hint 1</summary>
For each position, water level = min(max_left, max_right) - height[i].
</details>

<details>
<summary>Hint 2</summary>
Precompute max_left and max_right arrays for O(n) space, O(n) time solution.
</details>

<details>
<summary>Hint 3</summary>
For O(1) space, use two pointers from both ends and track left_max and right_max.
</details>

## Function Signature

```rust
impl Solution {
    pub fn trap(height: Vec<i32>) -> i32 {
        
    }
}
```
