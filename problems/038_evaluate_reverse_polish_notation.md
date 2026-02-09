# 38. Evaluate Reverse Polish Notation
**Difficulty**: Medium  
**Topics**: Stack, Math

## Problem Description

You are given an array of strings `tokens` that represents an arithmetic expression in Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.

**Note:**
- Valid operators are `+`, `-`, `*`, and `/`.
- Each operand may be an integer or another expression.
- Division between two integers truncates toward zero.
- There will not be any division by zero.
- The input is guaranteed to be a valid RPN expression.

## Examples

### Example 1:
```
Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9
```

### Example 2:
```
Input: tokens = ["4","13","5","/","+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6
```

### Example 3:
```
Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
Output: 22
```

## Constraints

- `1 <= tokens.len() <= 10^4`
- `tokens[i]` is either an operator or an integer in the range `[-200, 200]`.

## Hints

<details>
<summary>Hint 1</summary>
Use a stack to store operands as you process the tokens.
</details>

<details>
<summary>Hint 2</summary>
When you encounter a number, push it. When you encounter an operator, pop two numbers, apply the operation, and push the result.
</details>

<details>
<summary>Hint 3</summary>
Be careful with the order of operands for subtraction and division: the second popped value is the left operand.
</details>

## Function Signature

```rust
impl Solution {
    pub fn eval_rpn(tokens: Vec<String>) -> i32 {
        
    }
}
```
