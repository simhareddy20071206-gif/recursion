

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
Here’s the **pseudocode** for the classic **“Print All Subsets of a Set”** problem using **recursion** 👇

---

## 🧩 **Problem:**

Given an array or string, print **all possible subsets** (the power set).

---

### **Idea (Recursion Logic)**

At each index, you have **two choices**:

1. **Include** the current element in the subset.
2. **Exclude** the current element and move to the next.

This naturally forms a recursion tree of size `2^n`.

---

### ✅ **Pseudocode**

```text
FUNCTION generateSubsets(arr, index, currentSubset):
    IF index == length(arr):
        PRINT currentSubset
        RETURN

    // Choice 1: Include current element
    currentSubset.add(arr[index])
    generateSubsets(arr, index + 1, currentSubset)

    // Backtrack (remove last added element)
    currentSubset.removeLast()

    // Choice 2: Exclude current element
    generateSubsets(arr, index + 1, currentSubset)
```

---

### 📘 **Example Dry Run**

Input: `arr = [1, 2]`

**Recursion Tree:**

```
generate(0, []) 
 ├─ Include 1 → generate(1, [1])
 │    ├─ Include 2 → generate(2, [1,2]) → print [1,2]
 │    └─ Exclude 2 → generate(2, [1]) → print [1]
 └─ Exclude 1 → generate(1, [])
      ├─ Include 2 → generate(2, [2]) → print [2]
      └─ Exclude 2 → generate(2, []) → print []
```

**Output:**

```
[1, 2]
[1]
[2]
[]
```

---

### ⚙️ **Time and Space Complexity**

| Type      | Complexity                                     |
| --------- | ---------------------------------------------- |
| **Time**  | O(2ⁿ) — every element can be included/excluded |
| **Space** | O(n) — recursion stack depth                   |

---

Perfect — you’re now moving to **Subset II**, a slightly advanced version 👏

---

## 🧩 **Problem: Subsets II**

You are given an array `nums` that **may contain duplicates**.
Return **all possible subsets (the power set)**, ensuring that **no duplicate subsets** appear in the output.

---

### 🧠 **Example**

**Input:**

```
nums = [1, 2, 2]
```

**All possible subsets (without duplicates):**

```
[]
[1]
[1,2]
[1,2,2]
[2]
[2,2]
```

---

## ⚙️ **Approach (Using Recursion + Backtracking)**

1. **Sort the array** — this helps easily skip duplicates.
2. At each recursive call:

   * You can **choose** to include or exclude each element.
3. **Skip duplicate elements** while exploring branches.

---

### ✅ **Pseudocode**

```text
FUNCTION subsetsWithDup(nums, index, currentSubset, result):
    ADD currentSubset TO result

    FOR i FROM index TO length(nums) - 1:
        IF i > index AND nums[i] == nums[i-1]:
            CONTINUE   // Skip duplicates

        currentSubset.add(nums[i])
        subsetsWithDup(nums, i + 1, currentSubset, result)
        currentSubset.removeLast()  // Backtrack
```

---

### ✅ **C++ Implementation**

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void helper(vector<int>& nums, int index, vector<int>& subset, vector<vector<int>>& result) {
    result.push_back(subset);

    for (int i = index; i < nums.size(); i++) {
        // Skip duplicates
        if (i > index && nums[i] == nums[i - 1]) continue;

        subset.push_back(nums[i]);
        helper(nums, i + 1, subset, result);
        subset.pop_back();  // Backtrack
    }
}

vector<vector<int>> subsetsWithDup(vector<int>& nums) {
    sort(nums.begin(), nums.end());   // Important for duplicate handling
    vector<vector<int>> result;
    vector<int> subset;
    helper(nums, 0, subset, result);
    return result;
}

int main() {
    vector<int> nums = {1, 2, 2};
    vector<vector<int>> result = subsetsWithDup(nums);

    for (auto& subset : result) {
        cout << "[ ";
        for (int val : subset) cout << val << " ";
        cout << "]" << endl;
    }
    return 0;
}
```

---

### 🧮 **Output**

```
[ ]
[ 1 ]
[ 1 2 ]
[ 1 2 2 ]
[ 2 ]
[ 2 2 ]
```

---

### ⏱ **Complexity**

| Type      | Complexity                                        |
| --------- | ------------------------------------------------- |
| **Time**  | O(2ⁿ) (though reduced due to skipping duplicates) |
| **Space** | O(n) recursion stack + O(2ⁿ) result storage       |

---




