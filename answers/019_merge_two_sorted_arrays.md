# Solution: Merge Two Sorted Arrays

## Complete Runnable Code

```rust
fn merge(nums1: &mut Vec<i32>, m: i32, nums2: &Vec<i32>, n: i32) {
    let (mut m, mut n) = (m as usize, n as usize);
    let mut p = m + n;  // Position to write (from the end)
    
    // Merge from the end to avoid overwriting
    while m > 0 && n > 0 {
        p -= 1;
        if nums1[m - 1] > nums2[n - 1] {
            nums1[p] = nums1[m - 1];
            m -= 1;
        } else {
            nums1[p] = nums2[n - 1];
            n -= 1;
        }
    }
    
    // If nums2 has remaining elements, copy them
    while n > 0 {
        p -= 1;
        nums1[p] = nums2[n - 1];
        n -= 1;
    }
    // If nums1 has remaining elements, they're already in place!
}

fn main() {
    // Test Case 1
    let mut nums1 = vec![1, 2, 3, 0, 0, 0];
    let nums2 = vec![2, 5, 6];
    println!("Before: nums1 = {:?}", nums1);
    println!("        nums2 = {:?}", nums2);
    merge(&mut nums1, 3, &nums2, 3);
    println!("After:  {:?}\n", nums1);
    // Output: [1, 2, 2, 3, 5, 6]
    
    // Test Case 2
    let mut nums1 = vec![1];
    let nums2: Vec<i32> = vec![];
    merge(&mut nums1, 1, &nums2, 0);
    println!("Merge with empty: {:?}\n", nums1);
    // Output: [1]
    
    // Test Case 3
    let mut nums1 = vec![0];
    let nums2 = vec![1];
    merge(&mut nums1, 0, &nums2, 1);
    println!("nums1 empty: {:?}\n", nums1);
    // Output: [1]
    
    // Test Case 4
    let mut nums1 = vec![4, 5, 6, 0, 0, 0];
    let nums2 = vec![1, 2, 3];
    merge(&mut nums1, 3, &nums2, 3);
    println!("All nums2 smaller: {:?}", nums1);
    // Output: [1, 2, 3, 4, 5, 6]
}
```

## How It Works

### The Key Insight: Merge from the End!

If we merge from the beginning, we'd overwrite elements in nums1 that we haven't processed yet. But merging from the **end** solves this!

### Step-by-Step for nums1=[1,2,3,0,0,0], nums2=[2,5,6]

```
Initial:
nums1 = [1, 2, 3, 0, 0, 0]
         m=3 elements    │
              └──────────┘ extra space for merge
nums2 = [2, 5, 6]

Pointers: m=3, n=3, p=6

Step 1: Compare nums1[2]=3 vs nums2[2]=6
        6 > 3, so place 6 at p-1=5
        nums1 = [1, 2, 3, 0, 0, 6]
        p=5, n=2

Step 2: Compare nums1[2]=3 vs nums2[1]=5
        5 > 3, place 5 at p-1=4
        nums1 = [1, 2, 3, 0, 5, 6]
        p=4, n=1

Step 3: Compare nums1[2]=3 vs nums2[0]=2
        3 > 2, place 3 at p-1=3
        nums1 = [1, 2, 3, 3, 5, 6]
        p=3, m=2

Step 4: Compare nums1[1]=2 vs nums2[0]=2
        2 == 2, place nums2[0]=2 at p-1=2
        nums1 = [1, 2, 2, 3, 5, 6]
        p=2, n=0

n=0, exit loop.
nums1[0..2] already in place.

Final: [1, 2, 2, 3, 5, 6] ✓
```

### Visual Representation

```
nums1 = [1, 2, 3, 0, 0, 0]
         ↑     ↑        ↑
         │     m        p (write position)
         │
         └─ we compare m-1 with n-1

nums2 = [2, 5, 6]
               ↑
               n

We fill nums1 from right to left!
```

### Why No Need to Copy Remaining nums1?

If we exhaust nums2, any remaining nums1 elements are already in their correct positions (the left part of the array)!

```
Example: nums1 = [1, 2, 3, _, _, _], nums2 = [4, 5, 6]

After placing 6, 5, 4:
nums1 = [1, 2, 3, 4, 5, 6]
         └──────┘
         Already in place!
```

## Complexity Analysis

- **Time Complexity**: O(m + n) - Each element processed exactly once
- **Space Complexity**: O(1) - Merge in-place, no extra array needed
