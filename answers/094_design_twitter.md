# Solution: Design Twitter
```rust
use std::collections::{HashMap, HashSet, BinaryHeap};
struct Twitter { time: i32, tweets: HashMap<i32, Vec<(i32, i32)>>, following: HashMap<i32, HashSet<i32>> }
impl Twitter {
    fn new() -> Self { Twitter { time: 0, tweets: HashMap::new(), following: HashMap::new() } }
    fn post_tweet(&mut self, user_id: i32, tweet_id: i32) { self.time += 1; self.tweets.entry(user_id).or_default().push((self.time, tweet_id)); }
    fn get_news_feed(&self, user_id: i32) -> Vec<i32> {
        let mut heap = BinaryHeap::new();
        let users: Vec<i32> = std::iter::once(user_id).chain(self.following.get(&user_id).into_iter().flatten().copied()).collect();
        for u in users { for &(t, id) in self.tweets.get(&u).unwrap_or(&vec![]).iter().rev().take(10) { heap.push((t, id)); } }
        (0..10).filter_map(|_| heap.pop().map(|(_, id)| id)).collect()
    }
    fn follow(&mut self, follower_id: i32, followee_id: i32) { self.following.entry(follower_id).or_default().insert(followee_id); }
    fn unfollow(&mut self, follower_id: i32, followee_id: i32) { self.following.entry(follower_id).or_default().remove(&followee_id); }
}
```
**Time**: O(k log k), **Space**: O(users * tweets)
