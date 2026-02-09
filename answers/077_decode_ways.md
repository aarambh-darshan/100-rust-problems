# Solution: Decode Ways
```rust
impl Solution {
    pub fn num_decodings(s: String) -> i32 {
        let bytes = s.as_bytes();
        if bytes[0] == b'0' { return 0; }
        let (mut prev2, mut prev1) = (1, 1);
        for i in 1..bytes.len() {
            let mut curr = 0;
            if bytes[i] != b'0' { curr = prev1; }
            let two = (bytes[i - 1] - b'0') * 10 + (bytes[i] - b'0');
            if two >= 10 && two <= 26 { curr += prev2; }
            prev2 = prev1; prev1 = curr;
        }
        prev1
    }
}
```
**Time**: O(n), **Space**: O(1)
