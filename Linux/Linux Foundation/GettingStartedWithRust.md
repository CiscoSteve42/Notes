Getting Started With Rust
========================
* Just some basic, low-effort notes for my Linux Foundation Course on Rust

Why Learn Rust?
---------------

### Memory Safety and the Borrow Checker

By working together, the ownership system and the borrow checker help you avoid several types of common mistakes:

   *  Null pointer dereferences: Rust ensures that variables that are supposed to refer to a location in memory do

   * Buffer overflows: Rust ensures you only accidentally read or write data within the boundaries of an array or a list

   * Memory safety vulnerabilities (including dangling pointers, double frees, buffer overflows, etc.)

   * Data races (including memory corruption and deadlocks)

   * Undefined behaviors

### Zero-Cost Abstractions

**Advanced Programming Concepts**

* **Option and Result Enums** These help you manage situations where a variable might not have a value, or an operation could fail. They allow you to write clear, safe code without slowing your program.

* **Pattern Matching** This is a way to check what kind of data you're dealing with and act accordingly. It's a more readable and safe way to handle conditional logic, and Rust optimizes it so that it's as fast as using traditional if statements.

* **Closures** These are functions you can create on the fly within your code, similar to "lambdas" in other languages. They help write concise, customizable code. And again, they're designed to keep your program going.

* **Generics** This feature lets you write flexible code with different data types. The beauty is that these adaptations are sorted out when you compile your code, not while running it, which keeps things speedy.

* **Iterators and Combinators** These tools help you work with sequences of data. They can make your code both more concise and more efficient. Functions like map, filter, and fold let you process data collections in a functional programming style without a speed penalty.

* **Resource Acquisition Is Initialization (RAII)** This is a principle Rust uses to manage resources like memory or file handles automatically. When these resources are no longer needed, Rust cleans them up for you, helping to prevent leaks and other issues without introducing any performance cost.


### Concurrency

* **Ownership Model**

    * Rust’s unique ownership model is foundational to its approach to concurrency. In Rust, each piece of data is owned by a single entity—be it a variable, function, or data structure. This guarantees that only one part of your program can change that data at any time, with some uncommon exceptions. When applied to a concurrent setting, this eliminates the notorious issue of data races. The ownership model ensures that when data is shared between multiple threads, only one line can have mutable access, making unintentional overwrites or out-of-order execution impossible.

* **Borrow Checker**

    * Just like in memory safety, the borrow checker shines in the context of concurrency. The tool enforces the ownership rules at compile-time, allowing only permissible data access and modification patterns. If a thread needs to read shared data, the borrow checker ensures that no other thread is simultaneously writing to it. Likewise, if a line needs to write to shared data, the borrow checker ensures that no other thread is reading or writing to that data simultaneously. The borrow checker is written to provide helpful error messages to guide you in writing better and safer code, which is a major differentiator from the C/C++ compilers.

* **Threads and Asynchronous Tasks**

    * While the ownership model and the borrow checker provide the theoretical framework, Rust also gives you the practical tools to write concurrent code. These include built-in support for threads and asynchronous tasks. The threading API in Rust’s standard library is straightforward and abstracts over the underlying operating system's threading capabilities. This makes it easier to spawn, control, and coordinate threads. Asynchronous programming in Rust is facilitated through the async/await syntax and supported by powerful libraries like tokio or async-std. This is particularly useful for handling I/O-bound tasks efficiently without resorting to the complexity and overhead of managing multiple operating system-level threads.

* **Compiler Guarantees**

    * The most comforting feature of Rust's approach to concurrency is the compile-time guarantees it offers. If you've adhered to the rules and your code compiles, you're assured that specific bugs, such as data races, are absent in your concurrent application. This level of assurance is unmatched in most other languages and provides developers with significant peace of mind.

    * Rust's thoughtful combination of ownership principles, borrowing rules, and practical concurrency primitives makes it an excellent choice for writing robust, concurrent software. This is particularly beneficial in performance-critical and safety-critical systems like network servers, real-time systems, and data processing engines, where speed and reliability are paramount.


### Expressive and Modern

* **Functional Programming Capabilities** Rust fully embraces functional programming concepts, incorporating features like higher-order functions, closures, and iterators. Higher-order functions allow for operations like map, filter, and fold, which can transform collections without using verbose loops. The concept of closures, also known as anonymous functions, offers a convenient way to encapsulate a piece of functionality and pass it around in your code. Iterators in Rust further enrich its functional programming capabilities, letting developers chain sequences of operations on collections expressively. This functional approach encourages a style of programming that focuses on transforming data through pure functions, leading to more accessible code to understand, test, and maintain.
* **Pattern Matching** Rust's pattern matching is a potent tool for developers dealing with complex data structures. Whether you're working with enums, structs, or tuples, pattern matching allows for the easy deconstruction and inspection of complex data types. This feature goes beyond merely extracting values from data structures; it improves code readability by structuring multiple data scenarios coherently and straightforwardly. For example, when working with different variants of an enum, pattern matching explicitly clarifies which case the code handles, thereby improving both readability and maintainability.

* **Algebraic Data Types** Enums in Rust are algebraic data types, enabling developers to define a type that can take on a finite set of distinct values. These algebraic data types are crucial when modeling complex relationships between entities or states within finite-state machines. They're also beneficial for defining custom error types that can capture a variety of failure conditions. With the compiler's support, which performs exhaustiveness checks, developers can write expressive, robust code less prone to errors.

* **Modern Syntax and Features** Rust's language design emphasizes modernity, featuring a clean and expressive syntax. It incorporates an array of modern language features like closures, trait-based generics, lifetimes, and the async/await syntax for asynchronous programming. Trait-based generics, for example, allow for code reuse across different data types without sacrificing type safety or incurring runtime costs. The language's lifetime system ensures that references are valid for the duration they're being used, adding a layer of safety without requiring a garbage collector.


### Ecosystem and Community

* **Cargo and Crates**

    * One of Rust's most impactful contributions to the programming world is its package manager, Cargo. Not only does Cargo handle package dependencies, but it also simplifies the build process, test execution, and documentation generation. Cargo boosts development speed and ensures reproducibility across different environments by acting as a centralized ecosystem for managing crates. Whether you're building a small CLI tool or a complex web application, Cargo streamlines the entire process. You can easily add dependencies with a single line in the Cargo.toml file and run various Cargo commands to build, test, and publish your project.

    * [Crates.io](Crates.io) serves as the official package repository, hosting various libraries and packages. From async programming with tokio to web frameworks like Rocket, the crates available are vast and specialized, catering to an array of development needs.

* **Frameworks and Libraries** Rust's ecosystem has frameworks and libraries that simplify tasks in various domains. In web development, frameworks like Rocket and Actix offer extensive features and middleware support, making building robust, high-performance web applications easier. For serialization and deserialization, Serde is the go-to library. Diesel provides a safe and extensible way to interact with databases in data storage and object relational mappers (ORM).

Beyond these, Rust's ecosystem extends to scientific computing, machine learning, embedded systems, and even blockchain technology. The availability of specialized libraries allows Rust to penetrate different industry sectors, making it a versatile choice for many applications.

* **Common IDEs and Tools** Rust has excellent tooling support, with plugins and extensions available for popular Integrated Development Environments (IDEs) like Visual Studio Code, IntelliJ IDEA, and Emacs. These IDEs provide features such as intelligent code completion, on-the-fly error checking, and debugging facilities that streamline the development workflow. There are also more specialized Rust tools, like Rust Analyzer, focusing exclusively on providing an enhanced Rust development experience.

* **Strong Community**

    * The Rust community is another pillar that supports the language's rapid growth. Not only is it welcoming and inclusive, but it also strongly emphasizes knowledge-sharing and mentorship. Official forums, Discord channels, and IRC are hubs for discussions, problem-solving, and collaboration. The community's commitment to quality is evident in the extensive documentation accompanying most Rust projects, including tutorials, example code, and best practices.

    * **Rustaceans** —members of the Rust community—actively contribute to the open-source ecosystem by maintaining popular crates, improving the language, or even evangelizing its use through articles and talks. This community-driven development amplifies Rust's strengths, creating a virtuous cycle of improvement and adoption.

    * Events like local Rust meetups, international conferences, and workshops offer spaces for developers to network, share knowledge, and stay updated on the latest Rust advancements. These events often feature expert talks, hands-on sessions, and community discussions, enriching the collective know-how and fostering a solid camaraderie among Rust enthusiasts.

    * Rust has established itself as a mature, reliable, and continually evolving programming language by providing a robust ecosystem and a vibrant community. The synergy between its powerful features, comprehensive tooling, and enthusiastic community makes it an increasingly attractive choice for new and experienced developers.

* **The Linux Kernel** To the surprise of some, Rust has been allowed into the Linux Kernel, which has historically been written in C and already tried adding a second language without success. You can read about the RCF request here along with some of the discussion. While the use of Rust for kernel modules is becoming commonplace, there are many discussions on the degree of Rust adoption. The discussion will continue for some time, if history is an example. Keeping track of Rust for Linux on GitHub may be helpful if you are interested in kernel development using Rust.


### WebAssembly (Wasm)

* **Performance** Rust's focus on zero-cost abstractions ensures you can write high-performance applications without sacrificing readability or maintainability.

* **Memory Safety** Rust's ownership model mitigates many issues related to memory safety, a significant concern in web applications susceptible to attacks like buffer overflows.

* **Ease of Integration** Tools like wasm-bindgen make it relatively straightforward to interact between Rust and JavaScript, allowing you to leverage the vast npm ecosystem.

* **Robust Ecosystem** Libraries tailored for Wasm development in Rust, such as wasm-pack and yew, simplify tasks ranging from packaging Rust code as Wasm modules to creating interactive web apps.


### Embedded systems

* **Resource Efficiency** Rust's absence of a garbage collector and efficient memory management makes it ideal for environments where resource usage must be minimized.

* **Safety Guarantees** The safety guarantees that come with Rust's type system are invaluable in embedded contexts, where a simple mistake can lead to catastrophic failures.

* **Concurrency** With its advanced concurrency features, Rust can handle multi-threaded tasks commonly encountered in embedded systems.

* **Robust Ecosystem** Specialized crates for embedded development, such as those for real-time operating systems (RTOS) and hardware abstraction layers (HAL), are readily available. You can browse many of these specialized crates in the [embedded category on crates.io](https://crates.io/categories/embedded).


### Cross-Platform Development

* **Platform Independence** 

One of Rust’s foundational philosophies is platform independence. This is facilitated through its standard libraries and APIs, which are built to abstract away most of the underlying platform-specific implementations.

* **Standard Libraries and APIs** Rust's standard libraries provide a unified way of accessing essential functionalities such as file I/O, threading, and networking. By using these standard APIs, developers can write operational code across Windows, macOS, and various Linux distributions without fussing over the nuances of each operating system.

* **Runtime Dependencies** Languages like Java and Python rely on a runtime or virtual machine to execute code, requiring an extra layer of software installed on the target system. Rust takes a different approach.

* **Standalone Executables** In Rust, the final product is usually a standalone executable. The absence of a runtime reduces the size of the deliverable and eliminates the need to install additional software. This is especially beneficial for constrained environments or platforms where installing a runtime might not be an option.

* **Undefined Behavior** Undefined behavior can be a significant stumbling block in cross-platform development. What may work on one platform due to some compiler optimizations could completely fail on another.

* **Memory Safety and Strict Compiler Checks** Rust's emphasis on memory safety and rigorous compiler checks protects against undefined behavior. When code compiles successfully in Rust, it is guaranteed to be devoid of a whole class of bugs that can result in undefined behavior. This offers a predictable and consistent performance across multiple platforms.

* **Cross-Compilation** Rust’s package manager and build tool, Cargo, simplifies this process by providing robust support for cross-compilation. Simple configuration changes allow you to develop your project for different targets from your primary development environment.

    * **Cargo's Support for Cross-Compilation** By combining platform abstraction, zero runtime dependencies, stringent checks against undefined behavior, and versatile build tools, Rust sets a new standard for cross-platform development. Its holistic approach ensures you can focus on implementing features rather than wrestling with platform-specific quirks.


Basic Rust Programs
-------------------

* [Rust Language Reference](https://doc.rust-lang.org/reference/index.html)

### Types of Tokens

* **Keywords**

    * **Strict Keywords** These are the backbone of Rust's syntax; they dictate how the fundamental building blocks like loops, conditionals, and functions are defined. For example, fn is used to define functions, let for declaring variables, and loop for infinite loops. Misusing these keywords will result in compile-time errors. 

    * **Reserved Keywords** While these words don't serve any purpose yet, they are reserved for future language expansions. Using them as identifiers will result in a compilation error, ensuring that future versions of Rust will not break existing codebases.

    * **Weak Keywords** These have a particular function but only under certain circumstances. For example, self is a weak keyword that refers to the instance on which a method is invoked, but it has no special meaning outside that context.


* **Identifiers** Identifiers are the customizable part of your code. You define what a variable or function is called and then use that name to refer to it throughout your code. Following naming conventions and keeping names descriptive can significantly improve the readability and maintainability of your code.

* **Literals** Literals let you embed simple values directly into your code. They are immutable and offer a performance advantage because they are evaluated simultaneously. Rust supports a range of literals, including numeric types (42, 3.14), text ('a', "hello"), and more complex ones like array and tuple literals ((1, 'a')).

* **Lifetimes** Lifetimes are perhaps one of the most groundbreaking features in Rust. Unlike garbage-collected or reference-counted languages, Rust uses lifetimes to manage memory safely at compile time. Understanding lifetimes is crucial for mastering Rust, as they ensure that references don't outlive the data they point to, avoiding *dangling references*.

* **Punctuation** Characters like ;, :, and others serve to structure your code. For example, semicolons (;) are used to terminate statements, and colons (:) are used to specify types. These may seem trivial, but they are critical in syntactically correcting the code.

* **Delimiters** 

    * **Curly Braces {}** These define a block of code. Everything between the {} is a separate scope. Variables declared inside are not accessible outside this block.

    * **Square Brackets []** Used in array declarations and for array indexing. For example, `let arr = [1, 2, 3];` declare an array, and `arr[0]` would access the first element.

    * **Parentheses ()** These are used in function declarations and calls to encapsulate parameters and arguments. They are also used to clarify the order of operations in mathematical expressions.


### Hello world

```rust
fn main() {
    println!("Low Taper Fade Meme is Massive");
}
// Hi Mom.
```

* **Function Declaration** *fn main()* signifies the primary function where execution begins. The keyword fn stands for 'function', and *main* is the function's name.

* **Curly Braces {}** These define the scope of the main function. All Rust functions have an opening { and a closing } to delineate their boundaries.

* **Standard Output** *println!()* is a macro that prints text to the standard output, typically your terminal or command prompt. The text to be printed is enclosed in double quotes (" ")

* **Semicolon ;** In Rust, a semicolon is used to signify the end of an expression that has an effect. It's the equivalent of a full stop in a sentence.

* **Comments** The // syntax initiates a line comment. Everything following // on the same line is ignored by the Rust compiler. This is great for adding short explanations or notes alongside your code.


### Factorial Calculation

```rust
fn factorial(n: u64) -> u64

    if n == 0 || n == 1 {
        1
    } else {
        n * factorial(n - 1)
    }
}

fn main() {
    let num: u64 = 69;
    let result = factorial(num)
    println!("Factorial of {} is: {}", num, result)
}
```

* **Function Definition** The fn factorial(n: u64) -> u64 { ... } syntax defines a function named factorial that takes one argument n of type u64 (unsigned 64-bit integer) and returns a value of the same type.

* **Base Case** Inside the function, we specify the base cases for n = 0 and n = 1. In mathematics, 0! = 1 and 1! = 1. Our function returns 1 for these cases.

* **Recursive Case** We employ recursion for values of n greater than 1. The factorial(n-1)) call performs the factorial calculation for n-1, and then we multiply the result by n.

* **Main Function** Here, we initialize a variable num of type u64 to 5. This is the number whose factorial we aim to calculate.

* **Function Call** We invoke our factorial function with num as an argument and store the result in a variable called result.

* **Output** Finally, we output the calculated factorial to the console using the println! macro, interpolating the value of num and result into the output string.


Basic Troubleshooting
---------------------

### Tools to Identify and Resolve Typos and Syntax errors

* **Rust Compiler (rustc)** The Rust compiler, rustc, is your first defense against syntax errors. When you compile your program, rustc flags any syntax errors, detailing each issue's line number and nature.

* **Clippy (Would you like some assistance today?)** Clippy is a linting tool that goes a step further, catching not just syntax errors, but also common programming mistakes, style issues, and more. You can run Clippy as a standalone command or integrate it into your editor. It analyzes your code and offers a plethora of warnings and suggestions, focusing on areas such as: 

    * **Simplified Code** Clippy recommends simpler, more readable code constructs.
    * **Unsafe Code** Flags unsafe code that could lead to undefined behavior.
    * **Performance** Suggests optimizations, like faster operation alternatives.
    * **Style Guidelines** Enforces consistent coding styles in line with Rust's best practices.
    * **Deprecated Items** Warns against the use of deprecated elements in the language.
    * **Error Handling** Recommends more idiomatic ways to handle errors.
    * **Redundant Code** Highlights and suggests removal of redundant code.
    * **Type Conversions** Flags unnecessary type conversions and advises on type appropriateness.
    * Pattern Matching: Provides guidance on making your code more expressive via better matching patterns.
    * **Complex Expressions** Suggests breaking down intricate expressions into simpler parts.

    * Clippy evolves with time, so the exact warnings may vary depending on your version.

    * **Warnings *ans* Suggestions Offered by Clippy**

       * **Unnecessary 'let' Binding** Clippy warns when you create a variable with let, but never use it.
        ```rust
        fn unnecessary_let() {
            let x = 42; // Clippy will warn about this unused binding
            println!("Hello, Rust!");
        }
        ```

        * **Unused Variable** Clippy warns when you declare a variable that is never used, even if it's not a let variable! Hey!
        ```rust
        fn unused_variable() {
            let x = 10 // Clippy be like "WTF BRAHHHHhh"
        }
        ```
        * **Unnecessary Cloning** Clippy will warn you when you use an unnecessary clone operation.
        ```rust
        fn unnecessary_cloning() {
            let name = "Alice";
            let _greeting = String::from(name.clone());
        // Clippy is Disappointed and will let you know 
        }
        ```
       
       * **Suspicious Operations** Clippy can catch potentially unintended operations.
       ```rust
       fn suspicious_operation(x: i32) {
           if x = 10 { // Clippy will warn you about using '=' instead of '==' in the if conditions
               println!("x is equal to 10");
           }  
       }
       ```

       * **Simplify Boolean Expressions** Clippy can suggest simplifying boolean expressions.
       ```rust
       fn simplify_boolean() {
           let condition = true;
           if condition == true { // Clippy will suggest simplifying this to just 'if condition'
               println!("Condition is true");
            }
       }
       ```

       * **Unnecessary Return** Clippy will warn when a function unnecessarily returns a value at the end.
        ```rust
        fn unnecessary_return(x: i32) -> i32 {
            if x > 0 {
                return x; // Clippy will warn you about this
            }
            0 // Instead, we can omit the 'return' keyword here
        }
        ```

        * **'if let' Instead of 'match'** Clippy may suggest using *match* instead of *if let* for better readability.
        ```rust
        fn if_let_instead_of_match() {
            let option_value = Some(42);
            if let Some(x) = option_value { // Clippy will suggest using a 'match' statement instead
                println!("Got value: {}", x);
            }
        }
        ```

        * **Manual 'collect()' on an Iterator** Clippy will suggest using the *collect()* method directly instead of using *collect()* with *FromIterator*.
        ```rust
        fn manual_collect() {
            let numbers = vec![1, 2, 3];
            let _vec: Vec<i32> = Vec::from_iter(numbers.iter().cloned());
            // Clippy will suggest that you use 'collect()'
        }xtagstartz
        ```

* **IDE and Code Editors** Laughs in NeoVim superiority

* **Rust Analyzer** This advanced language server provides real-time code analysis and integrates well with IDEs, offering instant feedback on errors and potential improvements. It can also be accessed via the command line and incorporated into text editors like Vim. Key features include:

    * **Auto-Completion** Offers context-aware code completion suggestions.

    * **Code Diagnostics** Highlights issues directly in the code editor.

    * **Find References and Go to Definition** Provides a quick navigation to definitions and usages.

    * **Documentation on Hover** Displays relevant documentation when hovering over code elements.

    * **Organize Imports** Automatically sorts and cleanus up your import statements.

    * **Rename Symbol** Safely renames variables and functions across your code. 

    * **Code Formatting** Uses *rustfmt* to format code according to Rust's guidelines. 

    * **Macro Expansion** Helps debug macros by showing how they expand.

* **Rustfmt** Though not directly related to troubleshooting, rustfmt improves code readability and can help avoid syntax errors by automatically formatting your code according to Rust's style guidelines.

* **Compile-Time Checks** The Rust type system and borrow checker identify many issues at compile-time, mitigating common issues like use-after-free and null pointer dereferences.

* **Testing** Writing unit and integration tests help catch syntax and logical errors, verifying that your code performs as intended.

* **Continuous Integration (CI)** CI pipelines like GitHub Actions or Travis CI help catch errors early by running automated tests and checks before merging the code.

* **Debugging Techniques** Rust offers excellent debugging support. You can use the println! or dbg! macros for debug prints, or specialized binaries like rust-gdb and rust-gdbgui for more complex debugging.


Cargo Package Manager
---------------------

### Initializing a New Project


