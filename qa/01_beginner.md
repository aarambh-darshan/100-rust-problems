# 🦀 Rust Interview Q&A - Beginner (1-40)

## Basics & Syntax

### 1. What is Rust?
**Answer:** Rust is a systems programming language developed by Mozilla that focuses on memory safety, speed, and concurrency. Unlike languages like C/C++, it guarantees memory safety at compile time without needing a garbage collector. It achieves this through its unique ownership system.

---

### 2. What are the key features of Rust?
**Answer:** The key features are: Memory safety without garbage collection, zero-cost abstractions (high-level features compile to efficient low-level code), fearless concurrency (the compiler prevents data races), pattern matching, type inference, and a minimal runtime making it suitable for embedded systems.

---

### 3. What is Cargo?
**Answer:** Cargo is Rust's official build system and package manager. It handles compiling your code, downloading dependencies (called crates), building those dependencies, and much more. It's like npm for JavaScript or pip for Python, but also handles building and testing.

---

### 4. What is a crate?
**Answer:** A crate is the smallest unit of code compilation in Rust. There are two types: binary crates which can be executed (they have a main function), and library crates which provide functionality to other crates but can't run on their own.

---

### 5. What is the difference between `let` and `const`?
**Answer:** `let` creates a runtime variable that can optionally be mutable, while `const` creates a compile-time constant that must have its type annotated and value known at compile time. Constants can never be mutable and are inlined by the compiler. You can shadow a `let` variable but not a `const`.

---

### 6. What is shadowing?
**Answer:** Shadowing allows you to declare a new variable with the same name as a previous variable, which "shadows" the original. Unlike mutation, shadowing creates a new variable, so you can even change the type. This is useful when you want to transform a value but keep the same name.

---

### 7. What are scalar types in Rust?
**Answer:** Scalar types represent single values. Rust has four: integers (signed and unsigned, from 8 to 128 bits), floating-point numbers (f32 and f64), booleans (true/false), and characters (which are 4 bytes and represent Unicode scalar values, not just ASCII).

---

### 8. What is the difference between String and &str?
**Answer:** String is an owned, heap-allocated, growable string that you can modify. &str (string slice) is a borrowed reference to string data - it's immutable and doesn't own its data. String literals are &str. Think of String as owning the text, and &str as just viewing text stored elsewhere.

---

### 9. What is the Option type?
**Answer:** Option represents a value that may or may not exist. It has two variants: Some containing a value, or None meaning no value. Rust uses Option instead of null pointers, which prevents null reference errors at compile time. You must explicitly handle both cases.

---

### 10. What is the Result type?
**Answer:** Result represents either success or failure of an operation. It has two variants: Ok containing the success value, or Err containing error information. It's used for recoverable errors and forces you to handle error cases explicitly, unlike exceptions in other languages.

---

## Ownership & Borrowing

### 11. What is ownership in Rust?
**Answer:** Ownership is Rust's core memory management concept with three rules: each value has exactly one owner, there can only be one owner at a time, and when the owner goes out of scope, the value is dropped (freed). This eliminates memory leaks and double-free errors without a garbage collector.

---

### 12. What is borrowing?
**Answer:** Borrowing lets you reference a value without taking ownership of it. You create a reference that "borrows" the value temporarily. The original owner keeps the value when the borrow ends. This allows multiple parts of code to access data without complicated ownership transfers.

---

### 13. What are the borrowing rules?
**Answer:** Two rules: First, you can have either multiple immutable references OR exactly one mutable reference at a time - never both. Second, references must always be valid (no dangling references). These rules prevent data races at compile time.

---

### 14. What is a lifetime?
**Answer:** A lifetime is the scope for which a reference is valid. Lifetimes ensure references don't outlive the data they point to. Most of the time Rust infers lifetimes, but sometimes you need to annotate them explicitly to tell the compiler how references relate to each other.

---

### 15. What is the 'static lifetime?
**Answer:** 'static means the reference can live for the entire duration of the program. String literals have static lifetime because they're embedded in the binary. It's the longest possible lifetime and is often used for constants or error messages.

---

### 16. What is the Copy trait?
**Answer:** Copy marks types that can be duplicated by simply copying their bits. When you assign a Copy type to another variable, it's copied rather than moved. Stack-only types like integers, booleans, and fixed-size arrays of Copy types implement Copy. Heap-allocated types like String don't.

---

### 17. What is the Clone trait?
**Answer:** Clone provides a method to explicitly create a deep copy of a value. Unlike Copy, cloning may be expensive as it might allocate memory. You must call clone() explicitly. Any type implementing Copy automatically implements Clone, but Clone doesn't imply Copy.

---

### 18. What is the difference between Copy and Clone?
**Answer:** Copy is implicit and automatic - assignment copies the value without any syntax. Clone is explicit - you must call .clone(). Copy is cheap (just bit copying), while Clone can be expensive (may involve heap allocation). Copy is for simple stack types; Clone works for any type.

---

### 19. What is a dangling reference?
**Answer:** A dangling reference is a pointer to memory that has been freed or invalidated. In C/C++, this causes undefined behavior. Rust's compiler prevents dangling references entirely - if you try to return a reference to a local variable, it won't compile.

---

### 20. What does the move keyword do?
**Answer:** Move forces a closure to take ownership of captured variables rather than borrowing them. This is essential when the closure needs to outlive the scope where it's created, like when spawning threads or returning closures from functions.

---

## Structs & Enums

### 21. What is a struct?
**Answer:** A struct is a custom data type that groups related values together under named fields. It's like a class without methods in other languages. You can add methods using impl blocks. Rust has regular structs, tuple structs (with unnamed fields), and unit structs (with no fields).

---

### 22. What are tuple structs?
**Answer:** Tuple structs are structs with unnamed fields, accessed by index rather than name. They're useful when you want a distinct type but field names aren't meaningful. Common use: creating newtypes to distinguish semantically different values of the same underlying type.

---

### 23. What is a unit struct?
**Answer:** A unit struct has no fields - it's zero-sized. They're useful for implementing traits when you don't need to store any data, like marker traits or stateless strategy patterns. They take no memory at runtime.

---

### 24. What is an enum in Rust?
**Answer:** An enum defines a type that can be one of several variants. Unlike enums in C/Java, Rust's enums can hold data in each variant - different amounts and types for each. They're powerful for modeling states and alternatives, like Option and Result.

---

### 25. What is pattern matching?
**Answer:** Pattern matching with match allows you to compare a value against patterns and execute code based on which pattern matches. It's exhaustive - you must handle all cases. It's more powerful than switch statements because it can destructure complex types and bind variables.

---

### 26. What is if let?
**Answer:** If let is syntactic sugar for matching a single pattern when you only care about one case. Instead of writing a full match with a catch-all arm, if let handles one pattern concisely. It's commonly used with Option when you only care about the Some case.

---

### 27. What is while let?
**Answer:** While let is a loop that continues while a pattern matches. It's useful for iterating while extracting values from something like a stack or queue - the loop continues as long as there's a value to extract, and stops when None is returned.

---

### 28. What is an impl block?
**Answer:** An impl block defines methods and associated functions for a type. Methods take self (the instance) as their first parameter. Associated functions don't take self and are called with :: syntax, like constructors. You can have multiple impl blocks for the same type.

---

### 29. What is self vs Self?
**Answer:** Lowercase self refers to the instance the method is called on - like "this" in other languages. Uppercase Self is an alias for the type being implemented - useful in constructors and trait implementations where you don't want to repeat the type name.

---

### 30. What is an associated function?
**Answer:** An associated function is defined in an impl block but doesn't take self as a parameter. It's associated with the type rather than an instance. Called using Type::function() syntax. Commonly used for constructors like String::new() or Vec::with_capacity().

---

## Error Handling

### 31. How does Rust handle errors?
**Answer:** Rust splits errors into recoverable (using Result type) and unrecoverable (using panic!). There are no exceptions. Recoverable errors must be explicitly handled - the compiler forces you to deal with them. Unrecoverable errors crash the program with a stack trace.

---

### 32. What is the ? operator?
**Answer:** The question mark operator is shorthand for error propagation. If a Result is Ok, it unwraps the value. If it's Err, it returns early from the function with that error. It makes error handling concise while keeping it explicit.

---

### 33. What is unwrap()?
**Answer:** Unwrap extracts the value from Ok or Some, but panics if it's Err or None. It's convenient for prototyping or when you're certain a value exists, but risky in production code because panics crash the program. Prefer explicit error handling.

---

### 34. What is expect()?
**Answer:** Expect is like unwrap but lets you provide a custom panic message. This makes debugging easier because the message can explain what went wrong. Still panics on Err/None, but with a more informative error message.

---

### 35. What is unwrap_or()?
**Answer:** Unwrap_or provides a default value if the Result is Err or Option is None. Instead of panicking, it returns the default. Useful when you have a sensible fallback value. The default is always evaluated, even if not needed.

---

### 36. What is unwrap_or_else()?
**Answer:** Like unwrap_or but takes a closure that's only called if needed. This is more efficient when computing the default is expensive - the closure only runs on Err/None. You can also use the error value in the closure.

---

### 37. What is ok_or()?
**Answer:** Ok_or converts an Option to a Result. If it's Some, you get Ok with the value. If it's None, you get Err with the error you provide. Useful when you need to return a Result but have an Option.

---

### 38. When should you use panic!?
**Answer:** Use panic for unrecoverable errors: bugs in your code, invalid program state, or violations of invariants that shouldn't happen. Also fine in examples, tests, and prototypes. In library code, prefer returning Result so callers can decide how to handle errors.

---

### 39. What is map() on Result/Option?
**Answer:** Map transforms the success value inside Ok or Some using a function, leaving Err or None unchanged. It's for transforming values without unwrapping. Like applying a function "inside the container" without affecting error cases.

---

### 40. What is and_then()?
**Answer:** And_then chains operations that might fail. If the first Result is Ok, it calls your function with the value - that function returns another Result. If any step fails, the chain short-circuits with that error. Essential for composing fallible operations.
