# 14. Celsius to Fahrenheit
**Difficulty**: Easy  
**Topics**: Math

## Problem Description

Given a temperature in Celsius, convert it to Fahrenheit.

The formula is: `F = C × 9/5 + 32`

Return the result rounded to 2 decimal places.

## Examples

### Example 1:
```
Input: celsius = 0.0
Output: 32.0
Explanation: 0°C = 32°F (freezing point of water)
```

### Example 2:
```
Input: celsius = 100.0
Output: 212.0
Explanation: 100°C = 212°F (boiling point of water)
```

### Example 3:
```
Input: celsius = 37.0
Output: 98.6
Explanation: Normal human body temperature
```

## Constraints

- `-100.0 <= celsius <= 100.0`

## Hints

<details>
<summary>Hint 1</summary>
Apply the formula directly: F = C × 9/5 + 32
</details>

<details>
<summary>Hint 2</summary>
In Rust, be careful with integer vs floating-point division. Use 9.0/5.0 or 1.8.
</details>

<details>
<summary>Hint 3</summary>
To round to 2 decimal places, multiply by 100, round, then divide by 100.
</details>

## Function Signature

```rust
impl Solution {
    pub fn celsius_to_fahrenheit(celsius: f64) -> f64 {
        
    }
}
```
