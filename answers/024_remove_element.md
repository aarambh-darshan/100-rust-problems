# Solution: Remove Element

## Complete Runnable Code

```rust
fn remove_element(nums: &mut Vec<i32>, val: i32) -> i32 {
    let mut write = 0;  // Position to write next valid element
    
    for read in 0..nums.len() {
        if nums[read] != val {
            nums[write] = nums[read];
            write += 1;
        }
    }
    
    write as i32
}

fn main() {
    // Test Case 1
    let mut nums1 = vec![3, 2, 2, 3];
    let val1 = 3;
    let len1 = remove_element(&mut nums1, val1);
    println!("Remove {} from {:?}", val1, vec![3, 2, 2, 3]);
    println!("Result: {:?}, length = {}\n", &nums1[..len1 as usize], len1);
    // Output: [2, 2], length = 2
    
    // Test Case 2
    let mut nums2 = vec![0, 1, 2, 2, 3, 0, 4, 2];
    let val2 = 2;
    let len2 = remove_element(&mut nums2, val2);
    println!("Remove {} from {:?}", val2, vec![0, 1, 2, 2, 3, 0, 4, 2]);
    println!("Result: {:?}, length = {}\n", &nums2[..len2 as usize], len2);
    // Output: [0, 1, 3, 0, 4], length = 5
    
    // Test Case 3: All elements are val
    let mut nums3 = vec![2, 2, 2];
    let len3 = remove_element(&mut nums3, 2);
    println!("All same: length = {}\n", len3);
    // Output: 0
    
    // Test Case 4: No elements equal val
    let mut nums4 = vec![1, 3, 5];
    let len4 = remove_element(&mut nums4, 2);
    println!("None removed: {:?}, length = {}", &nums4[..len4 as usize], len4);
    // Output: [1, 3, 5], length = 3
}
```

## How It Works

### Two-Pointer Technique

- **read**: Scans through all elements
- **write**: Where to place the next valid element

```
val = 3
nums = [3, 2, 2, 3]
        R
        W

read=0: nums[0]=3 == val, skip (don't write)
        [3, 2, 2, 3]
        W  R

read=1: nums[1]=2 != val, copy to write position
        nums[0] = 2, write++
        [2, 2, 2, 3]
           W  R

read=2: nums[2]=2 != val, copy
        nums[1] = 2, write++
        [2, 2, 2, 3]
              W  R

read=3: nums[3]=3 == val, skip
        [2, 2, 2, 3]
              W     R(end)

Return: write = 2
Valid elements: [2, 2]
```

### Visual Representation

```
Before: [3, 2, 2, 3]
         ✗  ✓  ✓  ✗   (✗ = remove, ✓ = keep)

Process:
[3, 2, 2, 3]  →  read 3, skip
 ↑
[3, 2, 2, 3]  →  read 2, write to [0]
 W  R
[2, 2, 2, 3]  →  read 2, write to [1]
    W  R
[2, 2, 2, 3]  →  read 3, skip
       W  R

After: [2, 2, ?, ?]
        └──────┘ valid (k=2)
              └──┘ garbage (ignored)
```

### Key Points

1. **In-place modification**: We modify the array without extra space
2. **Order preserved**: Elements maintain their relative order
3. **Return value**: Length of valid portion (first k elements)

### Why This Works

We're essentially "compacting" the array - pushing all non-val elements to the front.

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass through the array
- **Space Complexity**: O(1) - Only using pointer variables
