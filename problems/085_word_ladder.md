# 85. Word Ladder
**Difficulty**: Hard  
**Topics**: Hash Table, String, BFS

## Problem Description

A **transformation sequence** from word `beginWord` to word `endWord` using a dictionary `wordList` is a sequence of words `beginWord -> s1 -> s2 -> ... -> sk` such that:

- Every adjacent pair of words differs by a single letter.
- Every `si` for `1 <= i <= k` is in `wordList`. Note that `beginWord` does not need to be in `wordList`.
- `sk == endWord`

Given two words, `beginWord` and `endWord`, and a dictionary `wordList`, return the **number of words** in the shortest transformation sequence from `beginWord` to `endWord`, or `0` if no such sequence exists.

## Examples

### Example 1:
```
Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]
Output: 5
Explanation: One shortest transformation is "hit" -> "hot" -> "dot" -> "dog" -> "cog" with 5 words.
```

### Example 2:
```
Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log"]
Output: 0
Explanation: The endWord "cog" is not in wordList, therefore no possible transformation.
```

## Constraints

- `1 <= beginWord.len() <= 10`
- `endWord.len() == beginWord.len()`
- `1 <= wordList.len() <= 5000`
- `wordList[i].len() == beginWord.len()`
- `beginWord`, `endWord`, and `wordList[i]` consist of lowercase English letters.
- `beginWord != endWord`
- All the words in `wordList` are **unique**.

## Hints

<details>
<summary>Hint 1</summary>
Use BFS - shortest path in an unweighted graph.
</details>

<details>
<summary>Hint 2</summary>
For each word, generate all possible one-letter transformations and check if they're in the word list.
</details>

<details>
<summary>Hint 3</summary>
Use a HashSet for O(1) word lookup. Remove visited words from the set to avoid revisiting.
</details>

## Function Signature

```rust
use std::collections::{HashSet, VecDeque};

impl Solution {
    pub fn ladder_length(begin_word: String, end_word: String, word_list: Vec<String>) -> i32 {
        
    }
}
```
