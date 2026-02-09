# 95. Find Median from Data Stream
**Difficulty**: Hard  
**Topics**: Two Pointers, Design, Sorting, Heap, Data Stream

## Problem Description

The **median** is the middle value in an ordered integer list. If the size of the list is even, there is no middle value, and the median is the mean of the two middle values.

Implement the MedianFinder class:

- `MedianFinder()` initializes the MedianFinder object.
- `add_num(num: i32)` adds the integer `num` from the data stream to the data structure.
- `find_median() -> f64` returns the median of all elements so far.

## Examples

### Example 1:
```
Input:
["MedianFinder", "addNum", "addNum", "findMedian", "addNum", "findMedian"]
[[], [1], [2], [], [3], []]
Output: [null, null, null, 1.5, null, 2.0]

Explanation:
MedianFinder medianFinder = new MedianFinder();
medianFinder.addNum(1);    // arr = [1]
medianFinder.addNum(2);    // arr = [1, 2]
medianFinder.findMedian(); // return 1.5 (i.e., (1 + 2) / 2)
medianFinder.addNum(3);    // arr = [1, 2, 3]
medianFinder.findMedian(); // return 2.0
```

## Constraints

- `-10^5 <= num <= 10^5`
- There will be at least one element in the data structure before calling `findMedian`.
- At most `5 * 10^4` calls will be made to `addNum` and `findMedian`.

## Hints

<details>
<summary>Hint 1</summary>
Use two heaps: a max-heap for the smaller half and a min-heap for the larger half.
</details>

<details>
<summary>Hint 2</summary>
Keep the heaps balanced: sizes differ by at most 1.
</details>

<details>
<summary>Hint 3</summary>
Median is either the top of the larger heap or the average of both tops.
</details>

## Function Signature

```rust
use std::collections::BinaryHeap;
use std::cmp::Reverse;

struct MedianFinder {
    small: BinaryHeap<i32>,          // max-heap (smaller half)
    large: BinaryHeap<Reverse<i32>>, // min-heap (larger half)
}

impl MedianFinder {
    fn new() -> Self {
        
    }
    
    fn add_num(&mut self, num: i32) {
        
    }
    
    fn find_median(&self) -> f64 {
        
    }
}
```
