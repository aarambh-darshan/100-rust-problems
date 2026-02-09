# 🦀 Rust Interview Q&A - Intermediate (41-80)

## Traits & Generics

### 41. What is a trait?
**Answer:** A trait defines shared behavior that types can implement - similar to interfaces in other languages but more powerful. Traits can have default method implementations, associated types, and constants. They're the foundation of Rust's polymorphism.

---

### 42. What are generics?
**Answer:** Generics allow you to write code that works with multiple types without duplicating it. The compiler generates specialized versions for each concrete type used. This gives you flexibility without runtime cost - it's called monomorphization.

---

### 43. What is a trait bound?
**Answer:** A trait bound restricts a generic type to only those implementing certain traits. It says "this function works with any type T, as long as T implements these traits." You can require multiple traits and use where clauses for complex bounds.

---

### 44. What is impl Trait?
**Answer:** Impl Trait in return position means "returns some type implementing this trait" without naming the specific type. It's useful when the exact type is complex or you want to hide implementation details. The concrete type is known at compile time.

---

### 45. What is a blanket implementation?
**Answer:** A blanket implementation implements a trait for all types satisfying certain bounds. For example, implementing Display for all types that implement Debug. It lets you add functionality to many types at once based on their capabilities.

---

### 46. What is dyn Trait?
**Answer:** Dyn Trait creates a trait object for dynamic dispatch. Instead of the compiler knowing the concrete type, it's determined at runtime through a virtual table. This enables heterogeneous collections but has a small runtime cost.

---

### 47. What is static vs dynamic dispatch?
**Answer:** Static dispatch resolves method calls at compile time - the compiler knows exactly which function to call. Dynamic dispatch uses a vtable at runtime. Static is faster but creates larger binaries. Dynamic is flexible but slightly slower.

---

### 48. What is the Default trait?
**Answer:** Default provides a standard "default value" for a type. For numbers it's zero, for booleans it's false, for Option it's None. You can derive it for structs where all fields implement Default. Useful for initialization and builder patterns.

---

### 49. What are From and Into traits?
**Answer:** From and Into enable type conversions. Implementing From for a type automatically gives you Into in reverse. They're for infallible conversions - if conversion might fail, use TryFrom and TryInto instead. They make APIs more ergonomic.

---

### 50. What is the Deref trait?
**Answer:** Deref lets you customize the dereference operator (*). It enables "deref coercion" where the compiler automatically converts types - like treating a Box like its contents or a String like a str. It makes smart pointers feel like regular references.

---

## Collections

### 51. What is Vec?
**Answer:** Vec is a growable array stored on the heap. It owns its elements and can add or remove items dynamically. Elements are stored contiguously in memory for cache efficiency. It's the most commonly used collection in Rust.

---

### 52. What is HashMap?
**Answer:** HashMap stores key-value pairs with O(1) average lookup time. Keys must implement Eq and Hash traits. It's unordered - iteration order isn't guaranteed. Values are owned by the map. Use it when you need fast lookup by key.

---

### 53. What is HashSet?
**Answer:** HashSet is a collection of unique values - like HashMap but only storing keys, no values. It provides fast membership testing and set operations like union, intersection, and difference. Elements must be hashable and comparable.

---

### 54. What is VecDeque?
**Answer:** VecDeque is a double-ended queue with efficient push and pop at both ends. Unlike Vec which is only efficient at the back, VecDeque uses a ring buffer for O(1) operations on both ends. Use it for queues or when you need to add to the front.

---

### 55. What is BinaryHeap?
**Answer:** BinaryHeap is a priority queue implemented as a max-heap. The largest element is always at the top. Elements must implement Ord. Use it when you repeatedly need the maximum element, like in Dijkstra's algorithm.

---

### 56. What is the Entry API?
**Answer:** The Entry API provides efficient "get or insert" operations for maps. Instead of looking up a key twice (to check then insert), entry does one lookup and returns a handle. You can then insert if missing, modify if present, or do both.

---

## Iterators

### 57. What is an iterator?
**Answer:** An iterator produces a sequence of values one at a time. It implements the Iterator trait with a next() method returning Option - Some for values, None when exhausted. Iterators are lazy - they don't do work until consumed.

---

### 58. What's the difference between iter(), iter_mut(), and into_iter()?
**Answer:** iter() borrows elements immutably, iter_mut() borrows mutably allowing modification, and into_iter() takes ownership consuming the collection. Choose based on whether you need to read, modify, or consume the elements.

---

### 59. What is map()?
**Answer:** Map transforms each element using a function, producing a new iterator. It's lazy - the function isn't called until you consume the iterator. Chain multiple maps for complex transformations. The original collection is unchanged.

---

### 60. What is filter()?
**Answer:** Filter keeps only elements matching a predicate function. It yields elements for which the predicate returns true. Like map, it's lazy and doesn't modify the original collection. Combine with map for powerful transformations.

---

### 61. What is fold()?
**Answer:** Fold combines all elements into a single value using an accumulator. You provide an initial value and a combining function. It's like reduce in other languages. Use it for sums, products, finding max/min, or building new structures.

---

### 62. What is collect()?
**Answer:** Collect consumes an iterator and creates a collection. The target collection type is inferred or specified. It can build Vec, HashMap, HashSet, String, and more. It's how you materialize lazy iterator chains into concrete data.

---

### 63. What are iterator adapters vs consumers?
**Answer:** Adapters transform iterators into new iterators - they're lazy and chain together. Consumers drive iteration and produce a final value. You build processing pipelines with adapters, then trigger execution with a consumer.

---

## Closures

### 64. What is a closure?
**Answer:** A closure is an anonymous function that can capture variables from its environment. Unlike regular functions, closures can access local variables from the scope where they're defined. The compiler infers parameter and return types.

---

### 65. What are Fn, FnMut, and FnOnce?
**Answer:** These traits describe how closures capture environment. Fn captures by reference and can be called repeatedly. FnMut captures by mutable reference and can modify captures. FnOnce takes ownership of captures and can only be called once.

---

### 66. How do closures capture variables?
**Answer:** Rust automatically chooses the least restrictive capture: immutable reference if possible, then mutable reference if needed, then ownership. The move keyword forces ownership capture, essential when closures must outlive their creation scope.

---

## Concurrency

### 67. How does Rust handle threads?
**Answer:** Rust uses OS threads with spawn(). The ownership system prevents data races at compile time - you can't accidentally share mutable data between threads. The type system enforces thread safety through Send and Sync traits.

---

### 68. What is the Send trait?
**Answer:** Send marks types safe to transfer between threads. Most types are Send. Non-Send types like Rc use non-atomic reference counting that isn't thread-safe. The compiler prevents sending non-Send types across thread boundaries.

---

### 69. What is the Sync trait?
**Answer:** Sync marks types safe to reference from multiple threads - meaning their references can be shared. If a type is Sync, immutable references to it are Send. RefCell isn't Sync because its runtime borrow checking isn't thread-safe.

---

### 70. What is Arc?
**Answer:** Arc is Atomic Reference Counted - a thread-safe version of Rc. Multiple threads can own the same data through Arc. The reference count uses atomic operations, making it safe but slightly slower than Rc. Use for shared ownership across threads.

---

### 71. What is Mutex?
**Answer:** Mutex provides mutual exclusion - only one thread can access the data at a time. You acquire a lock to access the data, others block until you release it. Rust's Mutex is safe - it can't be accessed without locking, and the lock auto-releases when dropped.

---

### 72. What is RwLock?
**Answer:** RwLock allows multiple readers or one writer. Many threads can read simultaneously since reading is safe. Writing requires exclusive access. More efficient than Mutex when reads vastly outnumber writes.

---

### 73. What are channels?
**Answer:** Channels enable message passing between threads. One side sends, the other receives. Messages are transferred, not shared. This models the "share by communicating" philosophy. Channels can be bounded or unbounded.

---

### 74. What is mpsc?
**Answer:** MPSC stands for Multiple Producer, Single Consumer. Many threads can send to one receiver. Senders can be cloned. It's the standard channel type in std. Good for task distribution - multiple workers sending results to one collector.

---

## Smart Pointers

### 75. What is Box?
**Answer:** Box allocates data on the heap with single ownership. Use it for recursive types (which need indirection), large data you don't want on the stack, or trait objects. It's the simplest smart pointer with no overhead beyond allocation.

---

### 76. What is Rc?
**Answer:** Rc is Reference Counted for single-threaded shared ownership. Multiple Rc pointers can own the same data. The data is freed when the last Rc is dropped. Not thread-safe - use Arc for threads. Immutable by default.

---

### 77. What is RefCell?
**Answer:** RefCell provides interior mutability - mutating data behind an immutable reference. It enforces borrowing rules at runtime instead of compile time. If rules are violated, it panics. Use when the compiler can't verify your safe borrowing patterns.

---

### 78. What is Cell?
**Answer:** Cell provides interior mutability for Copy types. You can get and set values without borrowing. It's simpler than RefCell - no runtime checks - but only works with types that can be copied. Useful for simple counters or flags.

---

### 79. What is Cow?
**Answer:** Cow is Clone-on-Write - it can hold either borrowed or owned data. It stays borrowed until you need to mutate, then clones to owned. Efficient when you usually only read data but occasionally need to modify it.

---

### 80. What is Pin?
**Answer:** Pin guarantees a value won't move in memory. Some types are self-referential - they contain pointers to themselves - and moving them would invalidate those pointers. Pin is essential for async/await where futures may be self-referential.
