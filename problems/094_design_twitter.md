# 94. Design Twitter
**Difficulty**: Hard  
**Topics**: Hash Table, Linked List, Design, Heap

## Problem Description

Design a simplified version of Twitter where users can post tweets, follow/unfollow another user, and see the 10 most recent tweets in their news feed.

Implement the `Twitter` class:

- `Twitter()` Initializes your twitter object.
- `post_tweet(userId: i32, tweetId: i32)` Composes a new tweet.
- `get_news_feed(userId: i32) -> Vec<i32>` Retrieves the 10 most recent tweet IDs in the user's news feed. Each item must be posted by users who the user followed or by the user themselves. Tweets must be **ordered from most recent to least recent**.
- `follow(followerId: i32, followeeId: i32)` The user with ID `followerId` started following the user with ID `followeeId`.
- `unfollow(followerId: i32, followeeId: i32)` The user with ID `followerId` unfollowed the user with ID `followeeId`.

## Examples

### Example 1:
```
Input:
["Twitter", "postTweet", "getNewsFeed", "follow", "postTweet", "getNewsFeed", "unfollow", "getNewsFeed"]
[[], [1, 5], [1], [1, 2], [2, 6], [1], [1, 2], [1]]
Output: [null, null, [5], null, null, [6, 5], null, [5]]
```

## Constraints

- `1 <= userId, followerId, followeeId <= 500`
- `0 <= tweetId <= 10^4`
- All the tweets have unique IDs.
- At most `3 * 10^4` calls will be made to `postTweet`, `getNewsFeed`, `follow`, and `unfollow`.

## Hints

<details>
<summary>Hint 1</summary>
Use a HashMap to store each user's tweets and their followed users.
</details>

<details>
<summary>Hint 2</summary>
Include a global timestamp to order tweets chronologically.
</details>

<details>
<summary>Hint 3</summary>
For getNewsFeed, use a max-heap to merge tweets from all followed users (including self).
</details>

## Function Signature

```rust
use std::collections::{HashMap, HashSet, BinaryHeap};

struct Twitter {
    time: i32,
    tweets: HashMap<i32, Vec<(i32, i32)>>, // user -> [(time, tweetId)]
    following: HashMap<i32, HashSet<i32>>, // user -> set of followees
}

impl Twitter {
    fn new() -> Self {
        
    }
    
    fn post_tweet(&mut self, user_id: i32, tweet_id: i32) {
        
    }
    
    fn get_news_feed(&self, user_id: i32) -> Vec<i32> {
        
    }
    
    fn follow(&mut self, follower_id: i32, followee_id: i32) {
        
    }
    
    fn unfollow(&mut self, follower_id: i32, followee_id: i32) {
        
    }
}
```
