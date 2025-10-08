# recursion
all ypes of recursive problem solving methods
Here are **complete and concise notes on Recursion in DSA**, perfect for JEE-level or beginner-to-intermediate coding prep 👇

---

## 🧠 **Recursion – Core Concept**

**Definition:**
Recursion is a technique where a function calls **itself** directly or indirectly to solve a smaller version of the same problem.

**Structure:**

```cpp
void func() {
    // Base Case (stopping condition)
    if (condition) return;
    
    // Recursive Case
    func(); // Function calling itself
}
```

---

## ⚙️ **Key Terms**

| Term               | Meaning                                                                       |
| ------------------ | ----------------------------------------------------------------------------- |
| **Base Case**      | Condition where recursion stops. Prevents infinite calls.                     |
| **Recursive Case** | The part where the function calls itself with smaller input.                  |
| **Stack Frame**    | Each recursive call creates a new function instance stored in the call stack. |
| **Stack Overflow** | Happens when there is no base case or infinite recursion.                     |

---

## 🧩 **Types of Recursion**

1. **Direct Recursion:**
   Function calls itself directly.

   ```cpp
   void fun() {
       fun();
   }
   ```

2. **Indirect Recursion:**
   Function A calls B, and B calls A.

   ```cpp
   void A() { B(); }
   void B() { A(); }
   ```

3. **Tail Recursion:**
   Recursive call is the **last** operation in the function.
   (Can be optimized to iteration)

   ```cpp
   void tail(int n) {
       if (n == 0) return;
       cout << n << " ";
       tail(n - 1);
   }
   ```

4. **Non-Tail Recursion:**
   Recursive call is **not the last** step.

   ```cpp
   void nonTail(int n) {
       if (n == 0) return;
       nonTail(n - 1);
       cout << n << " ";
   }
   ```

---

## 🔁 **Recursion Flow Example**

### Example 1: Print Numbers from 1 to N

```cpp
void print(int n) {
    if (n == 0) return;     // Base case
    print(n - 1);           // Recursive call
    cout << n << " ";       // Work after recursion
}
```

**Output:** `1 2 3 4 5`

🧠 *Call stack builds up until base case, then unwinds printing values.*

---

## 🧮 **Mathematical Examples**

### 1. Factorial

```cpp
int fact(int n) {
    if (n == 0) return 1;      // Base case
    return n * fact(n - 1);    // Recursive case
}
```

### 2. Fibonacci

```cpp
int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```

**⚠️ Problem:** Exponential time — repeated calls.
**✅ Fix:** Use **Dynamic Programming / Memoization**.

---

## 🧱 **Applications of Recursion**

| Area                | Example                             |
| ------------------- | ----------------------------------- |
| Mathematics         | Factorial, Fibonacci                |
| Searching/Sorting   | Binary Search, QuickSort, MergeSort |
| Backtracking        | N-Queens, Sudoku Solver             |
| Trees               | DFS Traversal, Height, Diameter     |
| Graphs              | DFS, Connected Components           |
| Divide & Conquer    | MergeSort, QuickSort                |
| Dynamic Programming | Subproblem recurrence               |

---

## ⚡ **Advantages**

* Simpler and cleaner code
* Natural fit for problems with self-similarity
* Easier implementation for tree/graph traversals

---

## ⚠️ **Disadvantages**

* High memory usage (stack space)
* Slower due to function call overhead
* Risk of stack overflow if base case missing

---

## 🧠 **Converting Recursion → Iteration**

* Use a **stack** (explicitly) to mimic recursion
* Useful for tail recursion → iteration optimization

---

## 🧩 **Common Recursion Patterns**

| Pattern                | Example                              |
| ---------------------- | ------------------------------------ |
| **Backtracking**       | Generating all subsets, permutations |
| **Divide & Conquer**   | Binary Search, MergeSort             |
| **Tree Recursion**     | Fibonacci, DFS in Trees              |
| **Indirect Recursion** | Mutual function calls                |

---

## 🧾 **Practice Problems**

| Problem                          | Platform             |
| -------------------------------- | -------------------- |
| Factorial of a number            | LeetCode / GFG       |
| Fibonacci sequence               | LeetCode             |
| Sum of first N numbers           | GFG                  |
| Reverse a string using recursion | GFG                  |
| Power function (xⁿ)              | LeetCode (Pow(x, n)) |
| Tower of Hanoi                   | GFG                  |
| Generate all subsets             | LeetCode #78         |
| Permutations of array            | LeetCode #46         |
| Binary Search (recursive)        | LeetCode #704        |
| Merge Sort / Quick Sort          | LeetCode / GFG       |

---

## 🧭 **Pro Tips**

1. Always write **base case first**.
2. Assume smaller problem works — **trust recursion**.
3. Dry-run using **recursion tree** or **stack trace**.
4. If problem asks for “all combinations/permutations” → likely **recursion/backtracking**.
5. Watch out for overlapping subproblems → use **memoization**.

---

Would you like me to create **handwritten-style summary notes (PDF)** or a **mind map** for this recursion topic?
I can generate either for easy revision.
