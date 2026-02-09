# Solution: Search Insert Position

## Complete Runnable Code

```rust
fn search_insert(nums: Vec<i32>, target: i32) -> i32 {
    let mut left = 0i32;
    let mut right = nums.len() as i32 - 1;
    
    while left <= right {
        let mid = left + (right - left) / 2;
        
        if nums[mid as usize] == target {
            return mid;
        } else if nums[mid as usize] < target {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    // If not found, 'left' is the insert position
    left
}

fn main() {
    // Test cases
    let nums = vec![1, 3, 5, 6];
    
    let targets = [5, 2, 7, 0, 6];
    
    println!("Array: {:?}\n", nums);
    println!("{:>8} | {:>8} | {:>20}", "Target", "Position", "Explanation");
    println!("{}", "-".repeat(45));
    
    for target in targets {
        let pos = search_insert(nums.clone(), target);
        let explanation = if nums.contains(&target) {
            "Found at index"
        } else {
            "Insert before index"
        };
        println!("{:>8} | {:>8} | {:>20}", target, pos, explanation);
    }
}
```

**Output:**
```
Array: [1, 3, 5, 6]

  Target | Position |          Explanation
---------------------------------------------
       5 |        2 |       Found at index
       2 |        1 |  Insert before index
       7 |        4 |  Insert before index
       0 |        0 |  Insert before index
       6 |        3 |       Found at index
```

## How It Works

### Binary Search with Insert Position

This is a modified binary search that returns:
- The index if target is found
- The position where target should be inserted if not found

### Step-by-Step for target=2 in [1, 3, 5, 6]

```
nums = [1, 3, 5, 6]
        0  1  2  3

left=0, right=3

Iteration 1:
  mid = (0+3)/2 = 1
  nums[1]=3 > 2
  right = 0

Iteration 2:
  mid = (0+0)/2 = 0
  nums[0]=1 < 2
  left = 1

left=1 > right=0 → Exit
Return: left = 1

Insert position: [1, *2*, 3, 5, 6]
                     ↑
                  index 1
```

### Visual Binary Search

```
Find insert position for 2 in [1, 3, 5, 6]

[1,  3,  5,  6]
 L       M   R     mid=1, 3>2, search left
 
[1,  3,  5,  6]
 LR  ↓           mid=0, 1<2, search right
 M
 
[1,  3,  5,  6]
     L              left=1, right=0, done!
 R

Insert at left=1: [1, 2, 3, 5, 6]
```

### Why Return 'left'?

After binary search completes:
- `left` points to the first element ≥ target
- This is exactly the insert position!

```
Case 1: [1, 3, 5], target=0
  → left=0 (insert at beginning)

Case 2: [1, 3, 5], target=2
  → left=1 (insert between 1 and 3)

Case 3: [1, 3, 5], target=6
  → left=3 (insert at end)
```

## Complexity Analysis

- **Time Complexity**: O(log n) - Binary search
- **Space Complexity**: O(1) - Only pointer variables
