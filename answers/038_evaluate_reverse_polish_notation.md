# Solution: Evaluate Reverse Polish Notation

## Complete Runnable Code

```rust
fn eval_rpn(tokens: Vec<String>) -> i32 {
    let mut stack: Vec<i32> = Vec::new();
    
    for token in tokens {
        match token.as_str() {
            "+" | "-" | "*" | "/" => {
                let b = stack.pop().unwrap();
                let a = stack.pop().unwrap();
                let result = match token.as_str() {
                    "+" => a + b,
                    "-" => a - b,
                    "*" => a * b,
                    "/" => a / b,  // Integer division truncates toward zero
                    _ => unreachable!(),
                };
                stack.push(result);
            }
            _ => {
                // It's a number
                stack.push(token.parse().unwrap());
            }
        }
    }
    
    stack.pop().unwrap()
}

fn main() {
    let test_cases = vec![
        vec!["2", "1", "+", "3", "*"],           // ((2 + 1) * 3) = 9
        vec!["4", "13", "5", "/", "+"],          // (4 + (13 / 5)) = 6
        vec!["10", "6", "9", "3", "+", "-11", "*", "/", "*", "17", "+", "5", "+"],
    ];
    
    for tokens in test_cases {
        let tokens_str: Vec<String> = tokens.iter().map(|s| s.to_string()).collect();
        let result = eval_rpn(tokens_str);
        println!("{:?}\n= {}\n", tokens, result);
    }
}
```

**Output:**
```
["2", "1", "+", "3", "*"]
= 9

["4", "13", "5", "/", "+"]
= 6

["10", "6", "9", "3", "+", "-11", "*", "/", "*", "17", "+", "5", "+"]
= 22
```

## How It Works

### Reverse Polish Notation (RPN)

Also called postfix notation - operators come AFTER operands:
- Infix: `(2 + 1) * 3`
- RPN: `2 1 + 3 *`

### Algorithm

1. See a number? Push to stack
2. See an operator? Pop two numbers, compute, push result

### Step-by-Step for ["2", "1", "+", "3", "*"]

```
Token "2": push 2
Stack: [2]

Token "1": push 1
Stack: [2, 1]

Token "+": pop 1 and 2, compute 2+1=3, push 3
Stack: [3]

Token "3": push 3
Stack: [3, 3]

Token "*": pop 3 and 3, compute 3*3=9, push 9
Stack: [9]

Final: 9
```

### Visual

```
Infix: (2 + 1) * 3

RPN evaluation:
  
  2      1      +       3      *
  ↓      ↓      ↓       ↓      ↓
 [2] → [2,1] → [3] → [3,3] → [9]
         ↑      ↑       ↑      ↑
       push   2+1=3   push   3*3=9
```

### Why RPN is Useful

- **No parentheses needed**
- **No operator precedence rules**
- **Easy to evaluate with a stack**

## Complexity Analysis

- **Time Complexity**: O(n) where n is number of tokens
- **Space Complexity**: O(n) for the stack
