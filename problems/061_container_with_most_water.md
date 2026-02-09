# 61. Container With Most Water
**Difficulty**: Medium  
**Topics**: Arrays, Two Pointers, Greedy

## Problem Description

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `i-th` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

**Notice** that you may not slant the container.

## Examples

### Example 1:
```
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The vertical lines are at indices 1 and 8. The container holds min(8,7) * (8-1) = 7 * 7 = 49 units of water.
```

### Example 2:
```
Input: height = [1,1]
Output: 1
```

## Constraints

- `n == height.len()`
- `2 <= n <= 10^5`
- `0 <= height[i] <= 10^4`

## Hints

<details>
<summary>Hint 1</summary>
Use two pointers starting from both ends of the array.
</details>

<details>
<summary>Hint 2</summary>
The area is limited by the shorter line. Move the pointer at the shorter line inward.
</details>

<details>
<summary>Hint 3</summary>
Calculate area = min(height[left], height[right]) * (right - left) at each step.
</details>

## Function Signature

```rust
impl Solution {
    pub fn max_area(height: Vec<i32>) -> i32 {
        
    }
}
```
