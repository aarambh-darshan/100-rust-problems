# Solution: Word Ladder
```rust
use std::collections::{HashSet, VecDeque};
impl Solution {
    pub fn ladder_length(begin_word: String, end_word: String, word_list: Vec<String>) -> i32 {
        let mut words: HashSet<_> = word_list.into_iter().collect();
        if !words.contains(&end_word) { return 0; }
        let mut queue = VecDeque::from([(begin_word, 1)]);
        while let Some((word, dist)) = queue.pop_front() {
            if word == end_word { return dist; }
            let chars: Vec<_> = word.chars().collect();
            for i in 0..chars.len() {
                for c in 'a'..='z' {
                    let mut new = chars.clone(); new[i] = c;
                    let new_word: String = new.into_iter().collect();
                    if words.remove(&new_word) { queue.push_back((new_word, dist + 1)); }
                }
            }
        }
        0
    }
}
```
**Time**: O(n * L²), **Space**: O(n * L)
