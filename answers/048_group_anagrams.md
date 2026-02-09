# Solution: Group Anagrams

## Complete Runnable Code

```rust
use std::collections::HashMap;

fn group_anagrams(strs: Vec<String>) -> Vec<Vec<String>> {
    let mut map: HashMap<Vec<u8>, Vec<String>> = HashMap::new();
    
    for s in strs {
        // Create sorted key
        let mut key: Vec<u8> = s.bytes().collect();
        key.sort();
        
        map.entry(key).or_default().push(s);
    }
    
    map.into_values().collect()
}

fn main() {
    let strs: Vec<String> = vec!["eat", "tea", "tan", "ate", "nat", "bat"]
        .into_iter()
        .map(String::from)
        .collect();
    
    let result = group_anagrams(strs);
    
    println!("Grouped anagrams:");
    for group in result {
        println!("  {:?}", group);
    }
}
```

**Output:**
```
Grouped anagrams:
  ["eat", "tea", "ate"]
  ["tan", "nat"]
  ["bat"]
```

## How It Works

### Sorted String as Key

Anagrams have the same letters, so sorting them gives same result:

```
"eat" → sort → "aet"
"tea" → sort → "aet"
"ate" → sort → "aet"

All map to same key "aet"!
```

### Visual

```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"]

HashMap:
  "aet" → ["eat", "tea", "ate"]
  "ant" → ["tan", "nat"]
  "abt" → ["bat"]
```

## Complexity

- **Time**: O(n * k log k) where k is max string length
- **Space**: O(n * k)
