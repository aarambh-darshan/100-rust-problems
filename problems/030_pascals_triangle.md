# 30. Pascal's Triangle
**Difficulty**: Easy  
**Topics**: Arrays, Dynamic Programming

## Problem Description

Given an integer `numRows`, return the first `numRows` of **Pascal's triangle**.

In Pascal's triangle, each number is the sum of the two numbers directly above it.

```
    1
   1 1
  1 2 1
 1 3 3 1
1 4 6 4 1
```

## Examples

### Example 1:
```
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```

### Example 2:
```
Input: numRows = 1
Output: [[1]]
```

## Constraints

- `1 <= numRows <= 30`

## Hints

<details>
<summary>Hint 1</summary>
Each row starts and ends with 1.
</details>

<details>
<summary>Hint 2</summary>
For row i, element j (where j > 0 and j < i) equals row[i-1][j-1] + row[i-1][j].
</details>

<details>
<summary>Hint 3</summary>
Build the triangle row by row, using the previous row to compute the current one.
</details>

## Function Signature

```rust
impl Solution {
    pub fn generate(num_rows: i32) -> Vec<Vec<i32>> {
        
    }
}
```
