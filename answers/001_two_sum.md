# Solution: Two Sum

## Complete Runnable Code

```rust
use std::collections::HashMap;

fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
    // Create a HashMap to store number -> index mapping
    let mut map: HashMap<i32, i32> = HashMap::new();
    
    // Iterate through each number with its index
    for (i, &num) in nums.iter().enumerate() {
        // Calculate what number we need to find
        let complement = target - num;
        
        // Check if we've seen the complement before
        if let Some(&j) = map.get(&complement) {
            // Found it! Return both indices
            return vec![j, i as i32];
        }
        
        // Store current number and its index for future lookups
        map.insert(num, i as i32);
    }
    
    // No solution found (shouldn't happen per problem constraints)
    vec![]
}

fn main() {
    // Test Case 1
    let nums1 = vec![2, 7, 11, 15];
    let target1 = 9;
    let result1 = two_sum(nums1, target1);
    println!("Test 1: {:?}", result1); // Output: [0, 1]
    
    // Test Case 2
    let nums2 = vec![3, 2, 4];
    let target2 = 6;
    let result2 = two_sum(nums2, target2);
    println!("Test 2: {:?}", result2); // Output: [1, 2]
    
    // Test Case 3
    let nums3 = vec![3, 3];
    let target3 = 6;
    let result3 = two_sum(nums3, target3);
    println!("Test 3: {:?}", result3); // Output: [0, 1]
}
```

## How It Works

### Step-by-Step Explanation

1. **Create a HashMap**: We use `HashMap<i32, i32>` where:
   - Key = the number we've seen
   - Value = the index where we saw it

2. **Iterate through the array**: For each number at index `i`:
   - Calculate `complement = target - num`
   - This is the number we need to find to make the sum equal to target

3. **Check if complement exists**: 
   - If `complement` is already in our HashMap, we found our answer!
   - Return `[index_of_complement, current_index]`

4. **Store the current number**: 
   - Add the current number and its index to the HashMap
   - This allows future numbers to find it as their complement

### Visual Example

```
nums = [2, 7, 11, 15], target = 9

i=0: num=2, complement=9-2=7
     HashMap is empty, 7 not found
     Add 2->0 to HashMap: {2: 0}

i=1: num=7, complement=9-7=2
     Check HashMap: 2 IS found at index 0! ✓
     Return [0, 1]
```

### Why HashMap?

| Approach | Time | Space |
|----------|------|-------|
| Brute Force (2 loops) | O(n²) | O(1) |
| HashMap (this solution) | O(n) | O(n) |

The HashMap gives us O(1) lookup time, making the overall algorithm O(n).

## Complexity Analysis

- **Time Complexity**: O(n) - We traverse the array once, and each HashMap operation is O(1)
- **Space Complexity**: O(n) - In worst case, we store all n elements in the HashMap
