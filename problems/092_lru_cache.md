# 92. LRU Cache
**Difficulty**: Hard  
**Topics**: Hash Table, Linked List, Design, Doubly-Linked List

## Problem Description

Design a data structure that follows the constraints of a **Least Recently Used (LRU) cache**.

Implement the `LRUCache` class:

- `LRUCache(capacity: i32)` Initialize the LRU cache with **positive** size `capacity`.
- `get(key: i32) -> i32` Return the value of the `key` if the key exists, otherwise return `-1`.
- `put(key: i32, value: i32)` Update the value of the `key` if the key exists. Otherwise, add the key-value pair to the cache. If the number of keys exceeds the `capacity` from this operation, **evict** the least recently used key.

The functions `get` and `put` must each run in **O(1)** average time complexity.

## Examples

### Example 1:
```
Input:
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"]
[[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]]
Output: [null, null, null, 1, null, -1, null, -1, 3, 4]

Explanation:
LRUCache lRUCache = new LRUCache(2);
lRUCache.put(1, 1); // cache is {1=1}
lRUCache.put(2, 2); // cache is {1=1, 2=2}
lRUCache.get(1);    // return 1
lRUCache.put(3, 3); // evicts key 2, cache is {1=1, 3=3}
lRUCache.get(2);    // returns -1 (not found)
lRUCache.put(4, 4); // evicts key 1, cache is {4=4, 3=3}
lRUCache.get(1);    // return -1 (not found)
lRUCache.get(3);    // return 3
lRUCache.get(4);    // return 4
```

## Constraints

- `1 <= capacity <= 3000`
- `0 <= key <= 10^4`
- `0 <= value <= 10^5`
- At most `2 * 10^5` calls will be made to `get` and `put`.

## Hints

<details>
<summary>Hint 1</summary>
Use a HashMap for O(1) access and a doubly linked list for O(1) insertion/deletion.
</details>

<details>
<summary>Hint 2</summary>
The most recently used items are at the head; the least recently used at the tail.
</details>

<details>
<summary>Hint 3</summary>
On access (get/put), move the item to the head. On eviction, remove from tail.
</details>

## Function Signature

```rust
use std::collections::HashMap;

struct LRUCache {
    capacity: usize,
    cache: HashMap<i32, i32>,
    order: Vec<i32>, // Simplified; actual impl uses doubly linked list
}

impl LRUCache {
    fn new(capacity: i32) -> Self {
        
    }
    
    fn get(&mut self, key: i32) -> i32 {
        
    }
    
    fn put(&mut self, key: i32, value: i32) {
        
    }
}
```
