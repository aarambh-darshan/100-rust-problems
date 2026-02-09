# Solution: Remove Duplicates from Sorted Array

## Complete Runnable Code

```rust
fn remove_duplicates(nums: &mut Vec<i32>) -> i32 {
    if nums.is_empty() {
        return 0;
    }
    
    // 'write' is the position where we'll place the next unique element
    let mut write = 1;
    
    // 'read' scans through the array looking for new unique elements
    for read in 1..nums.len() {
        // If current element is different from the last unique element
        if nums[read] != nums[write - 1] {
            nums[write] = nums[read];
            write += 1;
        }
    }
    
    write as i32
}

fn main() {
    // Test Case 1
    let mut nums1 = vec![1, 1, 2];
    let len1 = remove_duplicates(&mut nums1);
    println!("Array: {:?}", &nums1[..len1 as usize]);
    println!("Length: {}\n", len1);
    // Output: [1, 2], Length: 2
    
    // Test Case 2
    let mut nums2 = vec![0, 0, 1, 1, 1, 2, 2, 3, 3, 4];
    let len2 = remove_duplicates(&mut nums2);
    println!("Array: {:?}", &nums2[..len2 as usize]);
    println!("Length: {}\n", len2);
    // Output: [0, 1, 2, 3, 4], Length: 5
    
    // Test Case 3: Already unique
    let mut nums3 = vec![1, 2, 3];
    let len3 = remove_duplicates(&mut nums3);
    println!("Array: {:?}", &nums3[..len3 as usize]);
    println!("Length: {}\n", len3);
    
    // Test Case 4: All same
    let mut nums4 = vec![5, 5, 5, 5];
    let len4 = remove_duplicates(&mut nums4);
    println!("Array: {:?}", &nums4[..len4 as usize]);
    println!("Length: {}", len4);
}
```

## How It Works

### Two-Pointer Technique

We use two pointers:
- **write**: Where to place the next unique element
- **read**: Scans through looking for unique elements

### Step-by-Step for [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]

```
Initial: [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]
          W  R

write=1, read=1: nums[1]=0 == nums[0]=0, skip
              [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]
                  W  R

read=2: nums[2]=1 != nums[0]=0, copy!
        nums[1] = 1, write=2
              [0, 1, 1, 1, 1, 2, 2, 3, 3, 4]
                  W     R

read=3,4: nums[3]=1 == nums[1]=1, skip

read=5: nums[5]=2 != nums[1]=1, copy!
        nums[2] = 2, write=3
              [0, 1, 2, 1, 1, 2, 2, 3, 3, 4]
                      W           R

read=6: skip (2==2)

read=7: nums[7]=3 != nums[2]=2, copy!
        nums[3] = 3, write=4
              [0, 1, 2, 3, 1, 2, 2, 3, 3, 4]
                          W              R

read=8: skip (3==3)

read=9: nums[9]=4 != nums[3]=3, copy!
        nums[4] = 4, write=5
              [0, 1, 2, 3, 4, 2, 2, 3, 3, 4]
                              W             R (end)

Final: [0, 1, 2, 3, 4, ...]
Return: 5 (first 5 elements are unique)
```

### Visual Representation

```
Before: [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]
         ↑  ↑  ↑        ↑     ↑     ↑
         │  │  └────────┼─────┼─────┼── duplicates
         │  │           │     │     │
         └──┴───────────┴─────┴─────┴── unique values

After:  [0, 1, 2, 3, 4, ?, ?, ?, ?, ?]
         └──────────────┘
         k=5 unique elements
         (rest is garbage, ignore)
```

### Why This Works

1. Array is **sorted**, so duplicates are adjacent
2. We only need to compare with the last unique element
3. We overwrite duplicates with new unique values

### Key Insight

The problem asks to modify **in-place** — we don't create a new array, just reorganize the existing one!

## Complexity Analysis

- **Time Complexity**: O(n) - Single pass through the array
- **Space Complexity**: O(1) - Only using two pointer variables
