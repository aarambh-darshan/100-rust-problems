# 54. First Bad Version
**Difficulty**: Medium  
**Topics**: Binary Search, Interactive

## Problem Description

You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have `n` versions `[1, 2, ..., n]` and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API `bool is_bad_version(version)` which returns whether `version` is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

## Examples

### Example 1:
```
Input: n = 5, bad = 4
Output: 4
Explanation:
call is_bad_version(3) -> false
call is_bad_version(5) -> true
call is_bad_version(4) -> true
Then 4 is the first bad version.
```

### Example 2:
```
Input: n = 1, bad = 1
Output: 1
```

## Constraints

- `1 <= bad <= n <= 2^31 - 1`

## Hints

<details>
<summary>Hint 1</summary>
Use binary search to minimize API calls.
</details>

<details>
<summary>Hint 2</summary>
If is_bad_version(mid) is true, the first bad version is mid or before it.
</details>

<details>
<summary>Hint 3</summary>
If is_bad_version(mid) is false, the first bad version is after mid.
</details>

## Function Signature

```rust
// The API is_bad_version is defined for you.
// fn is_bad_version(version: i32) -> bool;

impl Solution {
    pub fn first_bad_version(&self, n: i32) -> i32 {
        
    }
}
```
