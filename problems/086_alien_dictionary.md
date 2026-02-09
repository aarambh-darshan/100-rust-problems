# 86. Alien Dictionary
**Difficulty**: Hard  
**Topics**: Array, String, DFS, BFS, Graph, Topological Sort

## Problem Description

There is a new alien language that uses the English alphabet. However, the order of the letters is unknown to you.

You are given a list of strings `words` from the alien language's dictionary. The strings in `words` are **sorted lexicographically** by the rules of this new language.

Return a string of the unique letters in the new alien language sorted in **lexicographically increasing order** by the new language's rules. If there is no solution, return `""`. If there are multiple solutions, return **any of them**.

## Examples

### Example 1:
```
Input: words = ["wrt","wrf","er","ett","rftt"]
Output: "wertf"
```

### Example 2:
```
Input: words = ["z","x"]
Output: "zx"
```

### Example 3:
```
Input: words = ["z","x","z"]
Output: ""
Explanation: The order is invalid, so return "".
```

## Constraints

- `1 <= words.len() <= 100`
- `1 <= words[i].len() <= 100`
- `words[i]` consists of only lowercase English letters.

## Hints

<details>
<summary>Hint 1</summary>
Build a directed graph from the ordering information between adjacent words.
</details>

<details>
<summary>Hint 2</summary>
Compare adjacent words character by character. The first difference gives an edge.
</details>

<details>
<summary>Hint 3</summary>
Use topological sort to get the ordering. If there's a cycle, return "".
</details>

## Function Signature

```rust
use std::collections::{HashMap, HashSet, VecDeque};

impl Solution {
    pub fn alien_order(words: Vec<String>) -> String {
        
    }
}
```
