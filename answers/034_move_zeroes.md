# Solution: Move Zeroes

## Complete Runnable Code

```rust
fn move_zeroes(nums: &mut Vec<i32>) {
    let mut write = 0;  // Position to write next non-zero
    
    // Move all non-zero elements to the front
    for read in 0..nums.len() {
        if nums[read] != 0 {
            nums.swap(write, read);
            write += 1;
        }
    }
}

fn main() {
    let test_cases = vec![
        vec![0, 1, 0, 3, 12],
        vec![0, 0, 1],
        vec![1, 2, 3],
        vec![0, 0, 0],
        vec![1],
        vec![0],
    ];
    
    for mut nums in test_cases {
        let original = nums.clone();
        move_zeroes(&mut nums);
        println!("{:?} → {:?}", original, nums);
    }
}
```

**Output:**
```
[0, 1, 0, 3, 12] → [1, 3, 12, 0, 0]
[0, 0, 1] → [1, 0, 0]
[1, 2, 3] → [1, 2, 3]
[0, 0, 0] → [0, 0, 0]
[1] → [1]
[0] → [0]
```

## How It Works

### Two-Pointer Swap

- **write**: Where to place next non-zero
- **read**: Scans for non-zero elements

```
[0, 1, 0, 3, 12]
 W  R

read=0: nums[0]=0, skip
read=1: nums[1]=1≠0, swap with write
        [1, 0, 0, 3, 12], write=1
           W     R

read=2: nums[2]=0, skip
read=3: nums[3]=3≠0, swap
        [1, 3, 0, 0, 12], write=2
              W     R

read=4: nums[4]=12≠0, swap
        [1, 3, 12, 0, 0], write=3
                   W     R(end)

Final: [1, 3, 12, 0, 0] ✓
```

### Visual Animation

```
Step 0: [0, 1, 0, 3, 12]
         W  R
         
Step 1: [1, 0, 0, 3, 12]  (swapped 0↔1)
            W  R
            
Step 2: [1, 0, 0, 3, 12]  (skip 0)
            W     R
            
Step 3: [1, 3, 0, 0, 12]  (swapped 0↔3)
               W     R
               
Step 4: [1, 3, 12, 0, 0]  (swapped 0↔12)
                   W     R
```

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass
- **Space Complexity**: O(1) - In-place swapping
