# 📚 Module: Arrays (Part - I) | Lecture 10: Pairs in Array

---

## 🎯 Problem: Find All Pairs in Array

### 💡 What is a Pair?

A **pair** is a combination of any two elements from the array:

```
Array: [2, 4, 6, 8, 10]

All possible pairs:
(2,4)  (2,6)  (2,8)  (2,10)
(4,6)  (4,8)  (4,10)
(6,8)  (6,10)
(8,10)
```

**Note:** (2,4) and (4,2) are considered the **same pair** - order doesn't matter

---

## 🧠 Understanding the Pattern

### 📊 Step-by-Step Pair Generation:

```
Array: [2, 4, 6, 8, 10]

Element 2 pairs with: 4, 6, 8, 10        → 4 pairs
Element 4 pairs with: 6, 8, 10           → 3 pairs
Element 6 pairs with: 8, 10              → 2 pairs
Element 8 pairs with: 10                 → 1 pair
Element 10 pairs with: (none)            → 0 pairs

Total: 4 + 3 + 2 + 1 = 10 pairs
```

**Key Insight:** Each element pairs only with elements **after** it (to avoid duplicates)

---

## 💻 Nested Loops Solution

### 🔧 The Logic:

**Outer Loop:** Go through each element  
**Inner Loop:** Pair current element with all elements **after** it

```java
for(int i = 0; i < n; i++) {
    for(int j = i + 1; j < n; j++) {
        // arr[i] and arr[j] form a pair
    }
}
```

### 🎨 Visual Representation:

```
i=0: j=1,2,3,4    → Pairs with (1), (2), (3), (4)
i=1: j=2,3,4      → Pairs with (2), (3), (4)
i=2: j=3,4        → Pairs with (3), (4)
i=3: j=4          → Pairs with (4)
i=4: j=(none)     → No more pairs
```

---

## 💻 Complete Code Implementation

### 🔧 Full Program:

```java
public class PairsInArray {
    
    public static void printPairs(int numbers[]) {
        
        int totalPairs = 0;
        
        // Outer loop: for each element
        for(int i = 0; i < numbers.length; i++) {
            
            // Inner loop: pair with elements after current
            for(int j = i + 1; j < numbers.length; j++) {
                
                // Print the pair
                System.out.print("(" + numbers[i] + "," + numbers[j] + ") ");
                
                // Count pairs
                totalPairs++;
            }
            
            // New line after each element's pairs
            System.out.println();
        }
        
        // Print total pairs
        System.out.println("Total pairs: " + totalPairs);
    }
    
    public static void main(String[] args) {
        
        int numbers[] = {2, 4, 6, 8, 10};
        
        System.out.println("Array: [2, 4, 6, 8, 10]\n");
        System.out.println("All pairs:");
        printPairs(numbers);
    }
}
```

### 📊 Output:
```
Array: [2, 4, 6, 8, 10]

All pairs:
(2,4) (2,6) (2,8) (2,10) 
(4,6) (4,8) (4,10) 
(6,8) (6,10) 
(8,10) 
Total pairs: 10
```

---

## 🔑 Why `j = i + 1` and NOT `j = 0`?

### ⚠️ Important Concept:

```java
for(int j = i + 1; j < n; j++)  // ✅ CORRECT
for(int j = 0; j < n; j++)      // ❌ WRONG - Creates duplicates
```

**The Difference:**

```
With j = 0:
i=0, j=0: (2,2)  ← Same element!
i=0, j=1: (2,4)
i=1, j=0: (4,2)  ← Duplicate of (2,4)
i=1, j=1: (4,4)  ← Same element!

With j = i+1:
i=0: (2,4), (2,6), (2,8), (2,10)
i=1: (4,6), (4,8), (4,10)
i=2: (6,8), (6,10)
i=3: (8,10)

No duplicates! ✅
```

---

## ⚠️ Common Mistake: Using `i++` Instead of `j++`

### 💥 WRONG CODE:

```java
for(int i = 0; i < numbers.length; i++) {
    for(int j = i + 1; j < numbers.length; i++) {  // ❌ BUG: i++ not j++!
        System.out.print("(" + numbers[i] + "," + numbers[j] + ") ");
    }
}
```

**Problem:** Inner loop increments `i` instead of `j`
- Result: **Infinite loop!**
- `j` never changes, condition always true

### ✅ CORRECT CODE:

```java
for(int i = 0; i < numbers.length; i++) {
    for(int j = i + 1; j < numbers.length; j++) {  // ✅ j++ is correct
        System.out.print("(" + numbers[i] + "," + numbers[j] + ") ");
    }
}
```

---

## 📊 Detailed Execution Trace

### 🎯 Array: `[2, 4, 6, 8, 10]`

```
Iteration 1: i=0, numbers[0]=2
  j=1: (2, 4)  totalPairs=1
  j=2: (2, 6)  totalPairs=2
  j=3: (2, 8)  totalPairs=3
  j=4: (2, 10) totalPairs=4
  Print newline

Iteration 2: i=1, numbers[1]=4
  j=2: (4, 6)  totalPairs=5
  j=3: (4, 8)  totalPairs=6
  j=4: (4, 10) totalPairs=7
  Print newline

Iteration 3: i=2, numbers[2]=6
  j=3: (6, 8)  totalPairs=8
  j=4: (6, 10) totalPairs=9
  Print newline

Iteration 4: i=3, numbers[3]=8
  j=4: (8, 10) totalPairs=10
  Print newline

Iteration 5: i=4, numbers[4]=10
  j=5: Condition false (5 not < 5)
  No pairs for 10

Final Output:
(2,4) (2,6) (2,8) (2,10)
(4,6) (4,8) (4,10)
(6,8) (6,10)
(8,10)
Total pairs: 10
```

---

## 📈 Total Pairs Formula

### 🔍 Mathematical Pattern:

```
For n elements, pairs with each:
Element 1: pairs with (n-1) elements
Element 2: pairs with (n-2) elements
Element 3: pairs with (n-3) elements
...
Element (n-1): pairs with 1 element
Element n: pairs with 0 elements

Total = (n-1) + (n-2) + (n-3) + ... + 1
      = Sum of (n-1) natural numbers
```

### 📊 Formula Derivation:

```
Sum of natural numbers = n × (n+1) / 2
Sum from 1 to (n-1) = (n-1) × n / 2

Therefore:
Total Pairs = n × (n-1) / 2
```

### 🎯 Examples:

```
n=5: TP = 5 × 4 / 2 = 10 ✅
n=4: TP = 4 × 3 / 2 = 6
n=3: TP = 3 × 2 / 2 = 3
n=2: TP = 2 × 1 / 2 = 1
n=1: TP = 1 × 0 / 2 = 0
```

---

## 💻 Program with Total Pairs Calculation

### 🔧 Using Formula:

```java
public class PairsWithFormula {
    
    public static void printPairs(int numbers[]) {
        
        System.out.println("All pairs:");
        int totalPairs = 0;
        
        for(int i = 0; i < numbers.length; i++) {
            for(int j = i + 1; j < numbers.length; j++) {
                System.out.print("(" + numbers[i] + "," + numbers[j] + ") ");
                totalPairs++;
            }
            System.out.println();
        }
        
        System.out.println("\nUsing loop count: " + totalPairs);
        
        // Using formula
        int n = numbers.length;
        int formulaPairs = n * (n - 1) / 2;
        System.out.println("Using formula: " + formulaPairs);
    }
    
    public static void main(String[] args) {
        
        int numbers[] = {2, 4, 6, 8, 10};
        
        System.out.println("Array: [2, 4, 6, 8, 10]");
        System.out.println("n = " + numbers.length + "\n");
        
        printPairs(numbers);
    }
}
```

### 📊 Output:
```
Array: [2, 4, 6, 8, 10]
n = 5

All pairs:
(2,4) (2,6) (2,8) (2,10) 
(4,6) (4,8) (4,10) 
(6,8) (6,10) 
(8,10) 

Using loop count: 10
Using formula: 10
```

---

## 🧪 Test Cases with Different Sizes

### ✅ Test Case 1: Even Size Array

```java
int[] arr = {1, 2, 3, 4};
// n=4, Total pairs = 4×3/2 = 6
// Pairs: (1,2), (1,3), (1,4), (2,3), (2,4), (3,4)
```

### ✅ Test Case 2: Odd Size Array

```java
int[] arr = {10, 20, 30};
// n=3, Total pairs = 3×2/2 = 3
// Pairs: (10,20), (10,30), (20,30)
```

### ✅ Test Case 3: Two Elements

```java
int[] arr = {5, 10};
// n=2, Total pairs = 2×1/2 = 1
// Pairs: (5,10)
```

### ✅ Test Case 4: Single Element

```java
int[] arr = {100};
// n=1, Total pairs = 1×0/2 = 0
// Pairs: (none)
```

---

## ⏱️ Time Complexity Analysis

### 🔍 Why O(n²)?

```
Outer loop: runs n times
Inner loop: 
  - 1st iteration: (n-1) times
  - 2nd iteration: (n-2) times
  - 3rd iteration: (n-3) times
  - ...
  - nth iteration: 0 times

Total iterations = (n-1) + (n-2) + ... + 1
                 = n(n-1)/2
                 = (n² - n)/2
                 = O(n²)
```

### 📊 Complexity Graph:

```
Operations
    |
 100|        O(n²)
    |       /
 50 |     /
    |   /
    | /
    |________________
    0   5   10   15  n
    
For n=10: ~50 operations
For n=20: ~200 operations
For n=100: ~5000 operations
```

---

## 🎨 Visual Algorithm Flow

```
┌─────────────────────────────────┐
│ Initialize:                     │
│ totalPairs = 0                  │
└────────────┬────────────────────┘
             ↓
┌─────────────────────────────────┐
│ Outer Loop: i from 0 to n-1     │
└────────────┬────────────────────┘
             ↓
┌─────────────────────────────────┐
│ Inner Loop: j from i+1 to n-1   │
└────────┬────────────────────────┘
         ↓
   ┌─────────────────┐
   │ Print Pair      │
   │ (arr[i], arr[j])│
   └────────┬────────┘
            ↓
   ┌─────────────────┐
   │ totalPairs++    │
   └────────┬────────┘
            ↓
   ┌─────────────────┐
   │ j++             │
   │ Inner loop      │
   │ condition check │
   └────┬────────┬───┘
       YES       NO
        ↓        ↓
      Loop    ┌──────────────┐
             │ Print newline│
             └────────┬─────┘
                      ↓
             ┌──────────────┐
             │ i++          │
             │ Outer check  │
             └──┬────────┬──┘
              YES        NO
               ↓          ↓
             Loop   Print total
```

---

## 📋 Key Concepts from Lecture 10

✅ **Nested loops for pair generation**  
✅ **Inner loop starts at i+1** to avoid duplicates  
✅ **Avoid common mistake: j++ not i++**  
✅ **Print newline after each element's pairs**  
✅ **Total pairs formula: n×(n-1)/2**  
✅ **Time Complexity: O(n²)**  
✅ **Space Complexity: O(1)**  

---

## 💡 Real-World Applications

| Application | Use |
|---|---|
| **Tournament pairings** | Match every player once |
| **Friend recommendations** | Suggest pairs of people |
| **Combination problems** | Mathematics & statistics |
| **Testing scenarios** | Test all combinations |
| **Graph theory** | Find all edges (pairs of nodes) |

---

## 🎯 Interview Perspective

### ❓ Possible Questions:

1. **"Print all pairs"** → Use code we learned
2. **"Count total pairs"** → Use formula n×(n-1)/2
3. **"Pairs with specific sum"** → Modify condition
4. **"Time complexity?"** → O(n²) because nested loops
5. **"Can you optimize?"** → Generally O(n²) is needed for all pairs

---

## 📊 Comparison Table

| Aspect | Details |
|---|---|
| **Approach** | Nested loops |
| **Outer Loop** | i from 0 to n-1 |
| **Inner Loop** | j from i+1 to n-1 |
| **Pairs** | (arr[i], arr[j]) |
| **Duplicates** | Avoided using i+1 |
| **Total Pairs** | n×(n-1)/2 |
| **Time** | O(n²) |
| **Space** | O(1) |

---

## ✨ Why This Pattern Matters

✅ **Foundation for many algorithms**  
✅ **Used in real interview questions**  
✅ **Basis for more complex problems**  
✅ **Teaches nested loops properly**  
✅ **Introduces complexity analysis**  

---

**Master nested loops and pair generation! 🎯**