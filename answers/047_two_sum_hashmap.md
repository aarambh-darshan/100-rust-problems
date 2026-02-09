# Solution: Two Sum with HashMap

## Complete Runnable Code

```rust
use std::collections::HashMap;

fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
    let mut map: HashMap<i32, usize> = HashMap::new();
    
    for (i, &num) in nums.iter().enumerate() {
        let complement = target - num;
        
        if let Some(&j) = map.get(&complement) {
            return vec![j as i32, i as i32];
        }
        
        map.insert(num, i);
    }
    
    vec![]
}

fn main() {
    let test_cases = vec![
        (vec![2, 7, 11, 15], 9),
        (vec![3, 2, 4], 6),
        (vec![3, 3], 6),
    ];
    
    for (nums, target) in test_cases {
        let result = two_sum(nums.clone(), target);
        println!("nums={:?}, target={} → indices {:?}", nums, target, result);
    }
}
```

**Output:**
```
nums=[2, 7, 11, 15], target=9 → indices [0, 1]
nums=[3, 2, 4], target=6 → indices [1, 2]
nums=[3, 3], target=6 → indices [0, 1]
```

## How It Works

### One-Pass HashMap

For each number, check if `target - num` exists in map.

```
target = 9, nums = [2, 7, 11, 15]

i=0, num=2: complement=7, not in map
    map = {2: 0}

i=1, num=7: complement=2, found at index 0!
    return [0, 1]
```

## Complexity

- **Time**: O(n)
- **Space**: O(n)
