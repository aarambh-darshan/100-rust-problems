# 91. Implement Trie (Prefix Tree)
**Difficulty**: Hard  
**Topics**: Hash Table, String, Design, Trie

## Problem Description

A **trie** (pronounced as "try") or **prefix tree** is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class:

- `Trie()` Initializes the trie object.
- `insert(word: String)` Inserts the string `word` into the trie.
- `search(word: String) -> bool` Returns `true` if the string `word` is in the trie (i.e., was inserted before), and `false` otherwise.
- `starts_with(prefix: String) -> bool` Returns `true` if there is a previously inserted string `word` that has the prefix `prefix`, and `false` otherwise.

## Examples

### Example 1:
```
Input:
["Trie", "insert", "search", "search", "startsWith", "insert", "search"]
[[], ["apple"], ["apple"], ["app"], ["app"], ["app"], ["app"]]
Output: [null, null, true, false, true, null, true]

Explanation:
Trie trie = new Trie();
trie.insert("apple");
trie.search("apple");   // return True
trie.search("app");     // return False
trie.startsWith("app"); // return True
trie.insert("app");
trie.search("app");     // return True
```

## Constraints

- `1 <= word.len(), prefix.len() <= 2000`
- `word` and `prefix` consist only of lowercase English letters.
- At most `3 * 10^4` calls in total will be made to `insert`, `search`, and `starts_with`.

## Hints

<details>
<summary>Hint 1</summary>
Each node in the trie can have up to 26 children (for each letter). Use a HashMap or array.
</details>

<details>
<summary>Hint 2</summary>
Each node should have a flag indicating if it marks the end of a word.
</details>

<details>
<summary>Hint 3</summary>
For insert/search/startsWith, traverse the trie character by character.
</details>

## Function Signature

```rust
use std::collections::HashMap;

#[derive(Default)]
struct TrieNode {
    children: HashMap<char, TrieNode>,
    is_end: bool,
}

struct Trie {
    root: TrieNode,
}

impl Trie {
    fn new() -> Self {
        
    }
    
    fn insert(&mut self, word: String) {
        
    }
    
    fn search(&self, word: String) -> bool {
        
    }
    
    fn starts_with(&self, prefix: String) -> bool {
        
    }
}
```
