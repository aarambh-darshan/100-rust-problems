# 100. N-Queens
**Difficulty**: Hard  
**Topics**: Array, Backtracking

## Problem Description

The **n-queens** puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return all distinct solutions to the **n-queens puzzle**. You may return the answer in **any order**.

Each solution contains a distinct board configuration of the n-queens' placement, where `'Q'` and `'.'` both indicate a queen and an empty space, respectively.

## Examples

### Example 1:
```
Input: n = 4
Output: [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
Explanation: There exist two distinct solutions to the 4-queens puzzle.
```

### Example 2:
```
Input: n = 1
Output: [["Q"]]
```

## Constraints

- `1 <= n <= 9`

## Hints

<details>
<summary>Hint 1</summary>
Use backtracking: try placing a queen in each row, one by one.
</details>

<details>
<summary>Hint 2</summary>
Track which columns, diagonals, and anti-diagonals are under attack.
</details>

<details>
<summary>Hint 3</summary>
For diagonals: cells on same diagonal have (row - col) constant. For anti-diagonals: (row + col) is constant.
</details>

## Function Signature

```rust
impl Solution {
    pub fn solve_n_queens(n: i32) -> Vec<Vec<String>> {
        
    }
}
```
