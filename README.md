# 🦀 100 Rust Problems

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Rust](https://img.shields.io/badge/Rust-1.70+-orange.svg)](https://www.rust-lang.org/)
[![Solutions](https://img.shields.io/badge/Solutions-Repo-blue.svg)](https://github.com/aarambh-darshan/rust-100-solutions)

A comprehensive Rust interview preparation resource featuring:
- **100 Coding Problems** with complete runnable solutions
- **120 Theoretical Q&A** covering Rust concepts from basics to advanced

> 🔗 **Practice Solutions**: [rust-100-solutions](https://github.com/aarambh-darshan/rust-100-solutions) - Fork it and solve problems yourself!

## ✨ Features

- **100 Coding Problems** covering all major DSA topics
- **120 Theory Q&A** - Ownership, Borrowing, Lifetimes, Async, Macros, Unsafe, FFI
- **Complete Solutions** with `main()` function - copy to [Rust Playground](https://play.rust-lang.org/) and run instantly
- **Step-by-step Explanations** with visual diagrams
- **Progressive Hints** (3 hints per problem)
- **Complexity Analysis** for all solutions


## 📁 Structure

```
100-rust-problems/
├── problems/     # 100 coding problem descriptions with hints
├── answers/      # Complete runnable solutions with explanations
├── qa/           # 120 theoretical interview Q&A
│   ├── 01_beginner.md      (Q1-40)
│   ├── 02_intermediate.md  (Q41-80)
│   └── 03_advanced.md      (Q81-120)
├── README.md     # This file
└── LICENSE       # MIT License
```

## 📊 Problem Categories

| Difficulty | Problems | Count |
|------------|----------|-------|
| 🟢 Beginner | 1-35 | 35 |
| 🟡 Intermediate | 36-70 | 35 |
| 🔴 Advanced | 71-100 | 30 |

## 📚 Interview Q&A (120 Questions)

| Level | Questions | Topics |
|-------|-----------|--------|
| 🟢 [Beginner](qa/01_beginner.md) | Q1-40 | Basics, Ownership, Borrowing, Structs, Enums, Error Handling |
| 🟡 [Intermediate](qa/02_intermediate.md) | Q41-80 | Traits, Generics, Collections, Iterators, Closures, Concurrency, Smart Pointers |
| 🔴 [Advanced](qa/03_advanced.md) | Q81-120 | Async/Await, Macros, Unsafe, FFI, Advanced Patterns, Testing |

---

## 🟢 Beginner (1-35)

### Basic Syntax & Math
| # | Problem | Topics |
|---|---------|--------|
| 1 | [Two Sum](problems/001_two_sum.md) | Arrays, HashMap |
| 2 | [Reverse String](problems/002_reverse_string.md) | Strings, Two Pointers |
| 3 | [Palindrome Number](problems/003_palindrome_number.md) | Math |
| 4 | [FizzBuzz](problems/004_fizzbuzz.md) | Math, Strings |
| 5 | [Fibonacci Number](problems/005_fibonacci_number.md) | Math, DP |
| 6 | [Factorial](problems/006_factorial.md) | Math, Recursion |
| 7 | [Count Digits](problems/007_count_digits.md) | Math |
| 8 | [Sum of Array](problems/008_sum_of_array.md) | Arrays |
| 9 | [Find Maximum](problems/009_find_maximum.md) | Arrays |
| 10 | [Find Minimum](problems/010_find_minimum.md) | Arrays |
| 11 | [Even or Odd](problems/011_even_or_odd.md) | Math |
| 12 | [Prime Number Check](problems/012_prime_number_check.md) | Math |
| 13 | [Leap Year](problems/013_leap_year.md) | Math |
| 14 | [Celsius to Fahrenheit](problems/014_celsius_to_fahrenheit.md) | Math |
| 15 | [Swap Two Numbers](problems/015_swap_two_numbers.md) | Variables |

### Arrays & Strings
| # | Problem | Topics |
|---|---------|--------|
| 16 | [Reverse Integer](problems/016_reverse_integer.md) | Math |
| 17 | [Count Vowels](problems/017_count_vowels.md) | Strings |
| 18 | [Remove Duplicates](problems/018_remove_duplicates_from_sorted_array.md) | Arrays, Two Pointers |
| 19 | [Merge Sorted Arrays](problems/019_merge_two_sorted_arrays.md) | Arrays |
| 20 | [Valid Parentheses](problems/020_valid_parentheses.md) | Stack, Strings |
| 21 | [Plus One](problems/021_plus_one.md) | Arrays, Math |
| 22 | [Sqrt(x)](problems/022_sqrt_x.md) | Binary Search, Math |
| 23 | [Climbing Stairs](problems/023_climbing_stairs.md) | DP |
| 24 | [Remove Element](problems/024_remove_element.md) | Arrays, Two Pointers |
| 25 | [Search Insert Position](problems/025_search_insert_position.md) | Binary Search |
| 26 | [Length of Last Word](problems/026_length_of_last_word.md) | Strings |
| 27 | [Add Binary](problems/027_add_binary.md) | Strings, Math |
| 28 | [Single Number](problems/028_single_number.md) | Bit Manipulation |
| 29 | [Best Time to Buy Stock](problems/029_best_time_to_buy_and_sell_stock.md) | Arrays, DP |
| 30 | [Pascal's Triangle](problems/030_pascals_triangle.md) | Arrays, DP |
| 31 | [Valid Anagram](problems/031_valid_anagram.md) | Strings, HashMap |
| 32 | [First Unique Character](problems/032_first_unique_character.md) | Strings, HashMap |
| 33 | [Intersection of Arrays](problems/033_intersection_of_two_arrays.md) | HashSet |
| 34 | [Move Zeroes](problems/034_move_zeroes.md) | Arrays, Two Pointers |
| 35 | [Power of Two](problems/035_power_of_two.md) | Bit Manipulation |

---

## 🟡 Intermediate (36-70)

### Data Structures
| # | Problem | Topics |
|---|---------|--------|
| 36 | [Implement Stack](problems/036_implement_stack.md) | Stack, Design |
| 37 | [Implement Queue](problems/037_implement_queue.md) | Queue, Design |
| 38 | [Evaluate RPN](problems/038_evaluate_reverse_polish_notation.md) | Stack |
| 39 | [Min Stack](problems/039_min_stack.md) | Stack, Design |
| 40 | [Reverse Linked List](problems/040_reverse_linked_list.md) | Linked List |
| 41 | [Merge Two Sorted Lists](problems/041_merge_two_sorted_lists.md) | Linked List |
| 42 | [Linked List Cycle](problems/042_linked_list_cycle.md) | Linked List, Two Pointers |
| 43 | [Middle of Linked List](problems/043_middle_of_linked_list.md) | Linked List |
| 44 | [Remove Nth From End](problems/044_remove_nth_from_end.md) | Linked List, Two Pointers |
| 45 | [Palindrome Linked List](problems/045_palindrome_linked_list.md) | Linked List |

### HashMaps & HashSets
| # | Problem | Topics |
|---|---------|--------|
| 46 | [Contains Duplicate](problems/046_contains_duplicate.md) | HashSet |
| 47 | [Two Sum HashMap](problems/047_two_sum_hashmap.md) | HashMap |
| 48 | [Group Anagrams](problems/048_group_anagrams.md) | HashMap, Strings |
| 49 | [Top K Frequent](problems/049_top_k_frequent_elements.md) | HashMap, Heap |
| 50 | [Longest Consecutive](problems/050_longest_consecutive_sequence.md) | HashSet |

### Binary Search & Sorting
| # | Problem | Topics |
|---|---------|--------|
| 51 | [Binary Search](problems/051_binary_search.md) | Binary Search |
| 52 | [Search Rotated Array](problems/052_search_in_rotated_sorted_array.md) | Binary Search |
| 53 | [Find Peak Element](problems/053_find_peak_element.md) | Binary Search |
| 54 | [First Bad Version](problems/054_first_bad_version.md) | Binary Search |
| 55 | [Search 2D Matrix](problems/055_search_2d_matrix.md) | Binary Search, Matrix |
| 56 | [Sort Colors](problems/056_sort_colors.md) | Sorting, Two Pointers |

### Arrays & Intervals
| # | Problem | Topics |
|---|---------|--------|
| 57 | [Merge Intervals](problems/057_merge_intervals.md) | Intervals, Sorting |
| 58 | [Insert Interval](problems/058_insert_interval.md) | Intervals |
| 59 | [Meeting Rooms](problems/059_meeting_rooms.md) | Arrays, Sorting |
| 60 | [3Sum](problems/060_3sum.md) | Arrays, Two Pointers |
| 61 | [Container With Most Water](problems/061_container_with_most_water.md) | Two Pointers |
| 62 | [Product Except Self](problems/062_product_of_array_except_self.md) | Arrays |
| 63 | [Maximum Subarray](problems/063_maximum_subarray.md) | Arrays, DP |
| 64 | [Spiral Matrix](problems/064_spiral_matrix.md) | Matrix |
| 65 | [Rotate Image](problems/065_rotate_image.md) | Matrix |
| 66 | [Set Matrix Zeroes](problems/066_set_matrix_zeroes.md) | Matrix |
| 67 | [Valid Sudoku](problems/067_valid_sudoku.md) | Matrix, HashSet |

### Backtracking
| # | Problem | Topics |
|---|---------|--------|
| 68 | [Subsets](problems/068_subsets.md) | Backtracking |
| 69 | [Permutations](problems/069_permutations.md) | Backtracking |
| 70 | [Combination Sum](problems/070_combination_sum.md) | Backtracking |

---

## 🔴 Advanced (71-100)

### Dynamic Programming
| # | Problem | Topics |
|---|---------|--------|
| 71 | [House Robber](problems/071_house_robber.md) | DP |
| 72 | [Coin Change](problems/072_coin_change.md) | DP |
| 73 | [Longest Increasing Subsequence](problems/073_longest_increasing_subsequence.md) | DP, Binary Search |
| 74 | [Unique Paths](problems/074_unique_paths.md) | DP |
| 75 | [Jump Game](problems/075_jump_game.md) | DP, Greedy |
| 76 | [Word Break](problems/076_word_break.md) | DP, HashSet |
| 77 | [Decode Ways](problems/077_decode_ways.md) | DP |
| 78 | [Longest Common Subsequence](problems/078_longest_common_subsequence.md) | DP |
| 79 | [Edit Distance](problems/079_edit_distance.md) | DP |
| 80 | [Maximal Square](problems/080_maximal_square.md) | DP, Matrix |

### Graph Algorithms
| # | Problem | Topics |
|---|---------|--------|
| 81 | [Number of Islands](problems/081_number_of_islands.md) | DFS, BFS, Matrix |
| 82 | [Clone Graph](problems/082_clone_graph.md) | DFS, Graph |
| 83 | [Course Schedule](problems/083_course_schedule.md) | Topological Sort |
| 84 | [Pacific Atlantic](problems/084_pacific_atlantic_water_flow.md) | DFS, Matrix |
| 85 | [Word Ladder](problems/085_word_ladder.md) | BFS |
| 86 | [Alien Dictionary](problems/086_alien_dictionary.md) | Topological Sort |
| 87 | [Graph Valid Tree](problems/087_graph_valid_tree.md) | Union Find |
| 88 | [Shortest Path Binary Matrix](problems/088_shortest_path_binary_matrix.md) | BFS |
| 89 | [Network Delay Time](problems/089_network_delay_time.md) | Dijkstra |
| 90 | [Minimum Spanning Tree](problems/090_minimum_spanning_tree.md) | Kruskal, Union Find |

### System Design & Advanced
| # | Problem | Topics |
|---|---------|--------|
| 91 | [Implement Trie](problems/091_implement_trie.md) | Trie, Design |
| 92 | [LRU Cache](problems/092_lru_cache.md) | Design, HashMap |
| 93 | [Serialize/Deserialize Tree](problems/093_serialize_deserialize_tree.md) | Tree, Design |
| 94 | [Design Twitter](problems/094_design_twitter.md) | Design, Heap |
| 95 | [Find Median Stream](problems/095_find_median_from_data_stream.md) | Heap, Design |
| 96 | [Sliding Window Maximum](problems/096_sliding_window_maximum.md) | Monotonic Queue |
| 97 | [Trapping Rain Water](problems/097_trapping_rain_water.md) | Two Pointers, Stack |
| 98 | [Merge K Sorted Lists](problems/098_merge_k_sorted_lists.md) | Heap, Linked List |
| 99 | [Regular Expression](problems/099_regular_expression_matching.md) | DP |
| 100 | [N-Queens](problems/100_n_queens.md) | Backtracking |

---

## 🚀 How to Use

1. **Start with Beginners**: If new to Rust, begin with problems 1-35
2. **Read the Problem**: Understand the description, examples, and constraints
3. **Try Before Hints**: Attempt solving before looking at hints
4. **Progressive Hints**: Each problem has 3 hints (easy → medium → strong)
5. **Run Solutions**: Copy any solution to [Rust Playground](https://play.rust-lang.org/) and run!

## 📝 Problem Format

Each problem file contains:
- **Difficulty** and **Topics**
- **Problem Description**
- **Examples** with input/output
- **Constraints**
- **3 Progressive Hints**
- **Function Signature** in Rust

## 🎯 Topics Covered

| Category | Topics |
|----------|--------|
| **Data Structures** | Arrays, Strings, LinkedList, Stack, Queue, HashMap, HashSet, Heap, Trie |
| **Algorithms** | Binary Search, Sorting, Two Pointers, Sliding Window, Backtracking |
| **Dynamic Programming** | 1D DP, 2D DP, Memoization |
| **Graphs** | DFS, BFS, Topological Sort, Dijkstra, Union Find, MST |
| **Design** | LRU Cache, Trie, Twitter, MedianFinder |

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs or issues
- Suggest new problems
- Improve solutions or explanations
- Fix typos

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Darshan Vichhi** ([@aarambh-darshan](https://github.com/aarambh-darshan))

---

⭐ **Star this repo if you find it helpful!**

Happy Coding! 🦀
