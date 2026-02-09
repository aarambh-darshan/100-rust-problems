# 🦀 Rust Interview Q&A - Advanced (81-120)

## Async/Await

### 81. What is async/await in Rust?
**Answer:** Async/await enables non-blocking concurrent programming. Async functions return Futures - values representing work that may complete later. Await pauses execution until a Future completes, but doesn't block the thread - other tasks can run meanwhile.

---

### 82. What is a Future?
**Answer:** A Future represents an asynchronous computation that will produce a value eventually. It's polled by the runtime. Poll returns Pending (not ready) or Ready (done). Futures are lazy - they don't start until awaited or spawned.

---

### 83. What is an async runtime?
**Answer:** Rust's standard library has no async runtime - you need external ones like Tokio or async-std. The runtime polls Futures, manages task scheduling, and handles I/O efficiently. Different runtimes have different features and tradeoffs.

---

### 84. What is spawning in async?
**Answer:** Spawning creates a new concurrent task that runs independently. Unlike await which pauses until completion, spawn starts something in the background. The spawned task runs concurrently, and you can await its result later if needed.

---

### 85. What is select?
**Answer:** Select races multiple Futures and continues with whichever completes first. Useful for timeouts, cancellation, or handling multiple event sources. The other Futures are dropped when one completes. Essential for responsive async programs.

---

### 86. What is join?
**Answer:** Join runs multiple Futures concurrently and waits for all to complete. Unlike running them sequentially with await, join allows them to progress simultaneously. Returns when everything is done, combining all results.

---

## Macros

### 87. What are macros in Rust?
**Answer:** Macros are metaprogramming - code that generates code at compile time. They reduce repetition and enable domain-specific syntax. Rust macros are hygienic, meaning they don't accidentally capture or interfere with variables in surrounding code.

---

### 88. What's the difference between declarative and procedural macros?
**Answer:** Declarative macros use pattern matching on syntax - simpler but less flexible. Procedural macros are functions that take token streams and produce new code - more powerful, used for derive macros and attribute macros. They're separate crates.

---

### 89. What are derive macros?
**Answer:** Derive macros automatically implement traits for types. The compiler generates implementation code based on the type's structure. Common derives include Debug, Clone, PartialEq. You can create custom derives for your own traits.

---

### 90. What are attribute macros?
**Answer:** Attribute macros transform annotated items - functions, structs, modules. They take the entire item as input and can modify, replace, or wrap it. Used for frameworks like Rocket for route handling or test frameworks.

---

### 91. What are function-like procedural macros?
**Answer:** These look like function calls but process arbitrary tokens. They can implement embedded domain-specific languages - like SQL validation at compile time. More flexible than declarative macros for complex parsing needs.

---

## Unsafe Rust

### 92. What is unsafe Rust?
**Answer:** Unsafe Rust allows operations the compiler can't verify - dereferencing raw pointers, calling unsafe functions, accessing mutable statics, implementing unsafe traits. It's needed for low-level operations. Unsafe doesn't disable all checks - lifetime and type rules still apply.

---

### 93. What are raw pointers?
**Answer:** Raw pointers are like C pointers - no lifetime tracking or safety guarantees. They can be null, dangling, or aliased. Creating them is safe; dereferencing requires unsafe. Used for FFI and building safe abstractions over low-level operations.

---

### 94. When should you use unsafe?
**Answer:** Use unsafe for FFI, performance-critical code where you can prove safety manually, implementing low-level primitives, and when the compiler is too conservative. Always wrap unsafe in safe abstractions. Comment why it's safe.

---

### 95. What is repr(C)?
**Answer:** Repr(C) tells the compiler to lay out a type exactly like C would - important for FFI. Without it, Rust might reorder fields for efficiency. Other repr options control size, alignment, and special optimizations.

---

## Memory & Performance

### 96. What is zero-cost abstraction?
**Answer:** Zero-cost means high-level features compile to code as efficient as hand-written low-level code. Iterators, closures, and generics have no runtime overhead. You don't pay for what you don't use, and what you do use costs nothing extra.

---

### 97. What is monomorphization?
**Answer:** Monomorphization is how generics work - the compiler creates specialized copies for each concrete type used. No runtime dispatch or type erasure. Fast execution but larger binaries. It's why generic Rust code matches specialized code in performance.

---

### 98. What does inline do?
**Answer:** Inline hints that a function's body should be copied to call sites. This eliminates function call overhead and enables further optimizations. The compiler makes final decisions. Critical for small functions used in hot paths.

---

### 99. What's the difference between stack and heap?
**Answer:** Stack is fast, automatic, fixed-size, LIFO allocation. Heap is dynamic, explicitly managed, accessed via pointers. Stack is for local variables with known size. Heap is for dynamically-sized data or data that outlives its creation scope.

---

### 100. How do you measure type sizes?
**Answer:** std::mem::size_of gives compile-time size in bytes. size_of_val gives runtime size for dynamically-sized types. Understanding sizes helps optimize memory layout and cache usage. Watch for padding in structs.

---

## Advanced Patterns

### 101. What is the newtype pattern?
**Answer:** Newtype wraps a type in a single-field struct for type safety. It creates a distinct type with zero runtime cost. Use it to prevent mixing semantically different values of the same underlying type, like meters vs kilometers.

---

### 102. What is the builder pattern?
**Answer:** Builder provides a fluent API for constructing complex objects step by step. Methods return self for chaining. A final build() method creates the object. Useful when objects have many optional fields or complex initialization.

---

### 103. What is the typestate pattern?
**Answer:** Typestate encodes object state in the type system. Different states are different types, and methods only exist on appropriate states. Invalid state transitions become compile errors. The state machine is enforced at compile time.

---

### 104. What is PhantomData?
**Answer:** PhantomData is a zero-sized type that tells the compiler about types or lifetimes that exist logically but not physically. Used in unsafe code to indicate ownership or lifetime relationships that aren't expressed in actual fields.

---

### 105. What are GATs (Generic Associated Types)?
**Answer:** GATs allow associated types to have their own generic parameters, especially lifetimes. They enable patterns like lending iterators that return references tied to the iterator's lifetime, not just the item's lifetime.

---

## Testing

### 106. How do you write tests in Rust?
**Answer:** Functions marked with #[test] are run by cargo test. They use assert macros to check conditions. Tests pass if they don't panic. Organize tests in a tests module in the same file or in a tests/ directory for integration tests.

---

### 107. What does cfg(test) do?
**Answer:** cfg(test) means code is only compiled when running tests. The tests module is typically marked this way. It lets you include test utilities and mocks that don't bloat the production binary. Tests can access private items.

---

### 108. What are integration tests?
**Answer:** Integration tests live in the tests/ directory and test your library as external users would - only public API is accessible. Each file is compiled as a separate crate. They verify that components work together correctly.

---

### 109. What are the assert macros?
**Answer:** assert! checks a boolean condition. assert_eq! checks equality and shows both values on failure. assert_ne! checks inequality. All accept optional format strings for custom messages. They panic on failure, failing the test.

---

### 110. What does the ignore attribute do?
**Answer:** #[ignore] skips a test during normal runs - for slow tests, tests requiring special setup, or work in progress. Run ignored tests explicitly with cargo test -- --ignored. Useful for separating quick checks from thorough tests.

---

## FFI

### 111. What is FFI?
**Answer:** Foreign Function Interface lets Rust call C code and vice versa. You declare external functions with extern blocks and call them in unsafe. Rust can also export functions for C to call. It's how Rust integrates with existing libraries and systems.

---

### 112. How do you export Rust functions to C?
**Answer:** Mark functions with #[no_mangle] to preserve the name and extern "C" for C calling convention. The function becomes callable from C. You can also build Rust as a static or dynamic library for linking with C programs.

---

### 113. What is no_mangle?
**Answer:** Rust mangles function names (adds type info for uniqueness). #[no_mangle] disables this, keeping the exact name you wrote. Essential for FFI where C code needs to find functions by specific names.

---

## Modules & Organization

### 114. How does the module system work?
**Answer:** Modules organize code into namespaces. Declare with mod, make public with pub. Modules can be inline or in separate files. The file structure mirrors the module hierarchy. Use statements bring items into scope.

---

### 115. What are the visibility modifiers?
**Answer:** pub is public everywhere. pub(crate) is public within the current crate only. pub(super) is public to the parent module. pub(in path) is public to a specific ancestor. Default is private to the current module.

---

### 116. What's the difference between mod and use?
**Answer:** mod declares that a module exists and loads it. use creates shortcuts to items for convenient access. You mod once to define structure, then use as needed. mod affects the module tree; use affects local naming.

---

### 117. What are workspaces?
**Answer:** Workspaces let multiple related packages share dependencies and a target directory. They're defined in Cargo.toml with a members list. Good for large projects with multiple binaries or libraries that work together.

---

### 118. What are feature flags?
**Answer:** Feature flags enable optional compilation of code and dependencies. Defined in Cargo.toml, enabled by consumers. They allow optional functionality without forcing on all users. Use cfg attributes to conditionally compile.

---

### 119. What is no_std?
**Answer:** #![no_std] means no standard library - only the core library is available. Used for embedded systems, operating systems, bootloaders - environments without an OS. You lose heap allocation, I/O, and threading unless you provide them.

---

### 120. What is the prelude?
**Answer:** The prelude is a set of types and traits automatically imported into every module. It includes Option, Result, common traits like Clone and Iterator. You can define custom preludes for your crate to reduce boilerplate imports.
