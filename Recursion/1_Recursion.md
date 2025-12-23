# Introduction to Recursion

## Video Summary
This video (from the "Strivers A2Z DSA Course" by take U forward) is the first lesson on **Recursion**. It introduces the basic concept of recursion in a beginner-friendly way using simple examples. The video explains what recursion is, why we need a stopping condition (base case), what happens during function calls, and introduces important ideas like the **recursion tree** and **stack space**.

### Key Points Explained in the Video

1. **What is Recursion?**
   - Recursion happens when a **function calls itself**.
      - It keeps calling itself until a certain condition is met (this condition is called the **base case**).

      2. **Simple Example: Printing "1" infinitely**
         - If you write a function that prints "1" and then calls itself again without any stop condition, it will print forever.
            - This leads to **infinite recursion** and eventually a **stack overflow** error (the program runs out of memory).

            3. **Why Stack Overflow Happens**
               - Every time a function is called, it is pushed onto a **call stack** (a special area in memory).
                  - When the function finishes, it is popped off the stack.
                     - In infinite recursion, functions keep getting pushed but never pop → stack fills up → crash.

                     ```mermaid
                     flowchart TD
                         A[Main] --> B[f()]
                             B --> C[print 1]
                                 C --> D[f() again]
                                     D --> E[f() again]
                                         E --> F[...]
                                             style F fill:#f9f,stroke:#333,stroke-width:2px
                                                 subgraph Call Stack
                                                         A --> B --> D --> E --> F
                                                             end
                                                             ```

                                                             4. **Base Case is Must**
                                                                - Without a base case, recursion never stops.
                                                                   - The base case tells the function: "If this condition is true, stop calling yourself and return."

                                                                   5. **Recursion Tree**
                                                                      - Visual way to understand how recursive calls branch out.
                                                                         - Each call creates new branches until base cases are reached.

                                                                         ```mermaid
                                                                         graph TD
                                                                             A[f(5)] --> B[f(4)]
                                                                                 A --> C[Base work for 5]
                                                                                     B --> D[f(3)]
                                                                                         B --> E[Base work for 4]
                                                                                             D --> F[f(2)]
                                                                                                 D --> G[Base work for 3]
                                                                                                     style A fill:#bbf,stroke:#333
                                                                                                     ```

                                                                                                     6. **Stack Space**
                                                                                                        - Each recursive call uses some memory on the call stack.
                                                                                                           - Too many calls → high memory usage.
                                                                                                              - This is why deep recursion can cause problems.

                                                                                                              ## Practice Question

                                                                                                              **Question:**  
                                                                                                              Write a recursive function to print numbers from `N` down to `1`.  
                                                                                                              For example, if `N = 5`, the output should be:  
                                                                                                              ```
                                                                                                              5
                                                                                                              4
                                                                                                              3
                                                                                                              2
                                                                                                              1
                                                                                                              ```

                                                                                                              You must use recursion (the function should call itself). Include a proper base case to stop the recursion.

                                                                                                              ### Python

                                                                                                              ```python
                                                                                                              def print_decreasing(n):
                                                                                                                  if n == 0:          # Base case: stop when n reaches 0
                                                                                                                          return
                                                                                                                              print(n)            # Print current n
                                                                                                                                  print_decreasing(n - 1)  # Recursive call with n-1

                                                                                                                                  # Test
                                                                                                                                  print_decreasing(5)
                                                                                                                                  ```

                                                                                                                                  **Step-by-step Explanation (for beginners):**
                                                                                                                                  - We define a function `print_decreasing` that takes a number `n`.
                                                                                                                                  - The `if n == 0` is the **base case** – when n is 0, we do nothing and return (stop recursion).
                                                                                                                                  - First, we `print(n)` – this prints the current value.
                                                                                                                                  - Then we call the same function with `n-1` – this is the recursive call.
                                                                                                                                  - Python uses indentation (spaces) to define blocks. No braces needed.
                                                                                                                                  - Functions are defined with `def`, and we call it at the end to test.

                                                                                                                                  ### C

                                                                                                                                  ```c
                                                                                                                                  #include <stdio.h>

                                                                                                                                  void print_decreasing(int n) {
                                                                                                                                      if (n == 0) {       // Base case
                                                                                                                                              return;
                                                                                                                                                  }
                                                                                                                                                      printf("%d\n", n);  // Print current n
                                                                                                                                                          print_decreasing(n - 1);  // Recursive call
                                                                                                                                                          }

                                                                                                                                                          int main() {
                                                                                                                                                              print_decreasing(5);
                                                                                                                                                                  return 0;
                                                                                                                                                                  }
                                                                                                                                                                  ```

                                                                                                                                                                  **Step-by-step Explanation:**
                                                                                                                                                                  - We include `<stdio.h>` for `printf`.
                                                                                                                                                                  - Function is `void` because it returns nothing.
                                                                                                                                                                  - `{}` curly braces define the function body.
                                                                                                                                                                  - `printf("%d\n", n);` prints the number followed by a newline.
                                                                                                                                                                  - `main` is the entry point. We call the function from there.
                                                                                                                                                                  - Compared to Python, C requires explicit semicolons `;` and compiling.

                                                                                                                                                                  ### C++

                                                                                                                                                                  ```cpp
                                                                                                                                                                  #include <iostream>
                                                                                                                                                                  using namespace std;

                                                                                                                                                                  void print_decreasing(int n) {
                                                                                                                                                                      if (n == 0) {
                                                                                                                                                                              return;
                                                                                                                                                                                  }
                                                                                                                                                                                      cout << n << endl;          // Print with newline
                                                                                                                                                                                          print_decreasing(n - 1);
                                                                                                                                                                                          }

                                                                                                                                                                                          int main() {
                                                                                                                                                                                              print_decreasing(5);
                                                                                                                                                                                                  return 0;
                                                                                                                                                                                                  }
                                                                                                                                                                                                  ```

                                                                                                                                                                                                  **Step-by-step Explanation:**
                                                                                                                                                                                                  - Very similar to C, but we use `cout` from `<iostream>` for printing.
                                                                                                                                                                                                  - `using namespace std;` avoids writing `std::` everywhere.
                                                                                                                                                                                                  - `endl` adds a newline and flushes output.
                                                                                                                                                                                                  - C++ is like C but with more features (here we use the simpler C-style).

                                                                                                                                                                                                  ### Rust

                                                                                                                                                                                                  ```rust
                                                                                                                                                                                                  fn print_decreasing(n: i32) {
                                                                                                                                                                                                      if n == 0 {
                                                                                                                                                                                                              return;
                                                                                                                                                                                                                  }
                                                                                                                                                                                                                      println!("{}", n);
                                                                                                                                                                                                                          print_decreasing(n - 1);
                                                                                                                                                                                                                          }

                                                                                                                                                                                                                          fn main() {
                                                                                                                                                                                                                              print_decreasing(5);
                                                                                                                                                                                                                              }
                                                                                                                                                                                                                              ```

                                                                                                                                                                                                                              **Step-by-step Explanation:**
                                                                                                                                                                                                                              - `fn` defines a function. We specify type `i32` for the parameter.
                                                                                                                                                                                                                              - No semicolons needed after `return` or after blocks in some cases.
                                                                                                                                                                                                                              - `println!` is a macro (ends with `!`) that prints with newline.
                                                                                                                                                                                                                              - Rust is very strict about types and memory safety – great for beginners to learn good habits.
                                                                                                                                                                                                                              - Unlike Python, everything must have a type (here `i32` for integer).

                                                                                                                                                                                                                              ### Java

                                                                                                                                                                                                                              ```java
                                                                                                                                                                                                                              public class Main {
                                                                                                                                                                                                                                  public static void print_decreasing(int n) {
                                                                                                                                                                                                                                          if (n == 0) {
                                                                                                                                                                                                                                                      return;
                                                                                                                                                                                                                                                              }
                                                                                                                                                                                                                                                                      System.out.println(n);
                                                                                                                                                                                                                                                                              print_decreasing(n - 1);
                                                                                                                                                                                                                                                                                  }

                                                                                                                                                                                                                                                                                      public static void main(String[] args) {
                                                                                                                                                                                                                                                                                              print_decreasing(5);
                                                                                                                                                                                                                                                                                                  }
                                                                                                                                                                                                                                                                                                  }
                                                                                                                                                                                                                                                                                                  ```

                                                                                                                                                                                                                                                                                                  **Step-by-step Explanation:**
                                                                                                                                                                                                                                                                                                  - Everything must be inside a `class`. File name should match class name.
                                                                                                                                                                                                                                                                                                  - Functions are called `methods`. We use `static` so we can call without object.
                                                                                                                                                                                                                                                                                                  - `System.out.println(n);` prints with newline.
                                                                                                                                                                                                                                                                                                  - Java is verbose: needs class, public, types for everything.
                                                                                                                                                                                                                                                                                                  - Semicolons `;` are required at end of statements.

                                                                                                                                                                                                                                                                                                  ### JavaScript

                                                                                                                                                                                                                                                                                                  ```javascript
                                                                                                                                                                                                                                                                                                  function print_decreasing(n) {
                                                                                                                                                                                                                                                                                                      if (n === 0) {
                                                                                                                                                                                                                                                                                                              return;
                                                                                                                                                                                                                                                                                                                  }
                                                                                                                                                                                                                                                                                                                      console.log(n);
                                                                                                                                                                                                                                                                                                                          print_decreasing(n - 1);
                                                                                                                                                                                                                                                                                                                          }

                                                                                                                                                                                                                                                                                                                          print_decreasing(5);
                                                                                                                                                                                                                                                                                                                          ```

                                                                                                                                                                                                                                                                                                                          **Step-by-step Explanation:**
                                                                                                                                                                                                                                                                                                                          - `function` keyword defines a function.
                                                                                                                                                                                                                                                                                                                          - No types needed (JavaScript is dynamically typed like Python).
                                                                                                                                                                                                                                                                                                                          - `console.log(n);` prints to console (run in browser console or Node.js).
                                                                                                                                                                                                                                                                                                                          - We can call the function directly without a `main`.
                                                                                                                                                                                                                                                                                                                          - Semicolons are optional but good practice.
                                                                                                                                                                                                                                                                                                                          - Very similar to Python in simplicity.