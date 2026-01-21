# 📚 Module: Arrays (Part - I) | Lecture 09: Reverse an Array

---

## 🎯 Problem: Reverse an Array

### 💡 What Does "Reverse" Mean?

Transform array from one order to the opposite order:

```
Original Array:  [2, 4, 6, 8, 10]
Reversed Array:  [10, 8, 6, 4, 2]
```

**Goal:** Reverse **in-place** (without extra array)

---

## 🔍 Two Approaches

### ❌ Approach 1: Using Extra Array (Not Optimal)

```java
// Create new array
int reversed[] = new int[n];

// Copy elements backward
for(int i = n-1; i >= 0; i--) {
    reversed[n-1-i] = arr[i];
}

// Copy back to original
for(int i = 0; i < n; i++) {
    arr[i] = reversed[i];
}
```

**Problems:**
- ❌ Uses extra O(n) space
- ❌ Two loops needed
- ❌ Memory inefficient

---

### ✅ Approach 2: Two-Pointer Method (Optimal)

```
Concept: Swap elements from both ends moving inward

Before:     [2,   4,   6,   8,   10]
             ↑                   ↑
           first               last

After swap: [10,  4,   6,   8,   2]
                  ↑           ↑
                first       last

Continue until they meet in middle!
```

---

## 🧠 Algorithm: Two-Pointer Technique

### 📝 Step-by-Step Process:

```
1. Initialize:
   first = 0 (start)
   last = n - 1 (end)

2. While first < last:
   
   a) Swap arr[first] with arr[last]
      Using temp variable: temp = arr[last]
                          arr[last] = arr[first]
                          arr[first] = temp
   
   b) Move pointers:
      first++  (move right)
      last--   (move left)

3. Continue until first >= last
```

---

## 📊 Complete Walkthrough Example

### 🎯 Array: `[2, 4, 6, 8, 10]` (5 elements)

```
Initial State:
first=0, last=4
[2, 4, 6, 8, 10]
 ↑              ↑

Step 1: Swap arr[0] and arr[4]
temp = 10
arr[4] = 2
arr[0] = 10
Result: [10, 4, 6, 8, 2]
first++, last--

Step 2: first=1, last=3
[10, 4, 6, 8, 2]
     ↑        ↑
Swap arr[1] and arr[3]
temp = 8
arr[3] = 4
arr[1] = 8
Result: [10, 8, 6, 4, 2]
first++, last--

Step 3: first=2, last=2
[10, 8, 6, 4, 2]
        ↑
first == last? YES → Stop!

Final Result: [10, 8, 6, 4, 2] ✅
```

---

## 💻 Complete Code Implementation

### 🔧 Full Program:

```java
public class ReverseArray {
    
    public static void reverse(int numbers[]) {
        
        // Initialize two pointers
        int first = 0;
        int last = numbers.length - 1;
        
        // Swap elements from both ends
        while(first < last) {
            
            // Swap using temporary variable
            int temp = numbers[last];
            numbers[last] = numbers[first];
            numbers[first] = temp;
            
            // Move pointers
            first++;
            last--;
        }
    }
    
    // Helper function to print array
    public static void printArray(int numbers[]) {
        for(int i = 0; i < numbers.length; i++) {
            System.out.print(numbers[i] + " ");
        }
        System.out.println();
    }
    
    public static void main(String[] args) {
        
        // Create array
        int numbers[] = {2, 4, 6, 8, 10};
        
        System.out.println("Original Array:");
        printArray(numbers);
        
        // Reverse array
        reverse(numbers);
        
        System.out.println("Reversed Array:");
        printArray(numbers);
    }
}
```

### 📊 Output:
```
Original Array:
2 4 6 8 10 
Reversed Array:
10 8 6 4 2
```

---

## 🎯 Example with Even-Sized Array

### 🔄 Array: `[1, 2, 3, 4]` (4 elements)

```
Initial:
first=0, last=3
[1, 2, 3, 4]
 ↑        ↑

Step 1: Swap arr[0] and arr[3]
[4, 2, 3, 1]
 ↑        ↑
first=1, last=2

Step 2: Swap arr[1] and arr[2]
[4, 3, 2, 1]
    ↑  ↑
first=2, last=1

first >= last? YES → Stop!

Result: [4, 3, 2, 1] ✅
```

---

## 🔄 Understanding the Swap Mechanism

### 💡 Bucket Analogy:

```
Imagine three buckets:

Initial State:
┌─────────┐  ┌─────────┐  ┌─────────┐
│ First   │  │ Last    │  │ Temp    │
│ (4)     │  │ (10)    │  │ (empty) │
└─────────┘  └─────────┘  └─────────┘

Step 1: temp = numbers[last]
┌─────────┐  ┌─────────┐  ┌─────────┐
│ First   │  │ Last    │  │ Temp    │
│ (4)     │  │ (empty) │  │ (10)    │
└─────────┘  └─────────┘  └─────────┘

Step 2: numbers[last] = numbers[first]
┌─────────┐  ┌─────────┐  ┌─────────┐
│ First   │  │ Last    │  │ Temp    │
│ (4)     │  │ (4)     │  │ (10)    │
└─────────┘  └─────────┘  └─────────┘

Step 3: numbers[first] = temp
┌─────────┐  ┌─────────┐  ┌─────────┐
│ First   │  │ Last    │  │ Temp    │
│ (10)    │  │ (4)     │  │ (empty) │
└─────────┘  └─────────┘  └─────────┘

Swap Complete! ✅
```

---

## ⏱️ Complexity Analysis

### 📊 Time Complexity:

```
Loop iterations: n/2 (half the array)

But O(n/2) = O(n)

Therefore: Time Complexity = O(n)
```

### 📊 Space Complexity:

```
Extra variables used:
- first (1 integer)
- last (1 integer)
- temp (1 integer)

Total: 3 integers = O(1) Constant space

Therefore: Space Complexity = O(1)
```

---

## 📈 Comparison: Two Approaches

### 📋 Approach 1 vs Approach 2:

| Aspect | Extra Array | Two-Pointer |
|---|---|---|
| **Time** | O(n) | O(n) |
| **Space** | O(n) ❌ | O(1) ✅ |
| **Arrays Created** | 2 | 0 |
| **Efficiency** | Lower | Higher |
| **Scalability** | Poor (large arrays) | Excellent |

### 🎯 Why Two-Pointer is Better:

```
Array Size    Extra Space (App1)    Extra Space (App2)
────────────────────────────────────────────────────
100           400 bytes             12 bytes
1,000         4,000 bytes           12 bytes
10,000        40,000 bytes          12 bytes
100,000       400,000 bytes         12 bytes
1,000,000     4,000,000 bytes       12 bytes ← Huge difference!

Two-Pointer approach ALWAYS uses only 12 bytes! 🚀
```

---

## 🧪 Different Test Cases

### ✅ Test Case 1: Odd-Sized Array

```java
int arr[] = {1, 2, 3, 4, 5};
reverse(arr);
// Result: [5, 4, 3, 2, 1] ✅
```

### ✅ Test Case 2: Even-Sized Array

```java
int arr[] = {10, 20, 30, 40};
reverse(arr);
// Result: [40, 30, 20, 10] ✅
```

### ✅ Test Case 3: Single Element

```java
int arr[] = {42};
reverse(arr);
// Result: [42] ✅ (no change needed)
```

### ✅ Test Case 4: Two Elements

```java
int arr[] = {1, 2};
reverse(arr);
// Result: [2, 1] ✅
```

---

## 🔑 Why Loop Condition is `first < last` (Not `<=`)

### ⚠️ Important Distinction:

```java
while(first < last)   // ✅ CORRECT
while(first <= last)  // ❌ WRONG
```

**The difference:**

```
Array: [1, 2, 3, 4, 5]
       0  1  2  3  4

With first < last:
When first=2, last=2, condition is FALSE → Stop ✅
Middle element doesn't swap with itself

With first <= last:
When first=2, last=2, condition is TRUE → Swap
Middle element swaps with itself (pointless) ❌
```

---

## 💻 Complete Program with Print Function

### 🔧 Full Implementation:

```java
public class ReverseArrayComplete {
    
    public static void reverse(int numbers[]) {
        
        int first = 0;
        int last = numbers.length - 1;
        
        while(first < last) {
            
            // Swap logic
            int temp = numbers[last];
            numbers[last] = numbers[first];
            numbers[first] = temp;
            
            // Move pointers
            first++;
            last--;
        }
    }
    
    public static void printArray(int numbers[]) {
        System.out.print("[ ");
        for(int i = 0; i < numbers.length; i++) {
            System.out.print(numbers[i]);
            if(i < numbers.length - 1) {
                System.out.print(", ");
            }
        }
        System.out.println(" ]");
    }
    
    public static void main(String[] args) {
        
        // Test Case 1: Odd size
        int arr1[] = {2, 4, 6, 8, 10};
        System.out.println("Test Case 1 (Odd size):");
        System.out.print("Before: ");
        printArray(arr1);
        reverse(arr1);
        System.out.print("After:  ");
        printArray(arr1);
        
        System.out.println();
        
        // Test Case 2: Even size
        int arr2[] = {1, 2, 3, 4};
        System.out.println("Test Case 2 (Even size):");
        System.out.print("Before: ");
        printArray(arr2);
        reverse(arr2);
        System.out.print("After:  ");
        printArray(arr2);
    }
}
```

### 📊 Output:
```
Test Case 1 (Odd size):
Before: [ 2, 4, 6, 8, 10 ]
After:  [ 10, 8, 6, 4, 2 ]

Test Case 2 (Even size):
Before: [ 1, 2, 3, 4 ]
After:  [ 4, 3, 2, 1 ]
```

---

## 🎨 Visual Algorithm Flow

```
┌──────────────────────────────────┐
│ Initialize:                      │
│ first = 0, last = length - 1     │
└────────────┬─────────────────────┘
             ↓
┌──────────────────────────────────┐
│ first < last?                    │
└──┬──────────────────────────┬────┘
  NO                         YES
   ↓                          ↓
Done!              ┌──────────────────┐
                   │ Swap:            │
                   │ temp = arr[last] │
                   │ arr[last] = ...  │
                   │ arr[first]       │
                   │ arr[first] = temp│
                   └────────┬─────────┘
                            ↓
                   ┌──────────────────┐
                   │ first++          │
                   │ last--           │
                   └────────┬─────────┘
                            ↓
                    ┌──────────────────┐
                    │ Check condition  │
                    │ first < last?    │
                    └──┬───────────┬───┘
                      YES         NO
                       ↓           ↓
                    Loop      Complete!
```

---

## 🔑 Key Concepts from Lecture 09

✅ **Two-Pointer approach is optimal**  
✅ **Swap mechanism uses temp variable**  
✅ **Loop condition: first < last (not <=)**  
✅ **Time Complexity: O(n)**  
✅ **Space Complexity: O(1)** - Most important!  
✅ **Works in-place without extra array**  
✅ **Arrays are passed by reference** - Changes reflect in main  
✅ **Three variables sufficient:** first, last, temp  

---

## 💡 Why This Matters

### 📊 Real-World Impact:

```
Reversing 1 million element array:

Approach 1 (Extra Array):
- Extra 4MB of memory needed
- GC overhead
- Cache misses

Approach 2 (Two-Pointer):
- Only ~50 bytes extra
- No GC pressure
- Better cache performance

Approach 2 is clearly superior! 🚀
```

---

## 🎯 Important Takeaways

1. **Always optimize for space** when possible
2. **Two-pointer technique** is widely used in interviews
3. **Swapping** is fundamental operation
4. **In-place algorithms** are preferred
5. **Time same, Space better** = Better solution

---

## 📝 Homework Challenge

Try reversing these arrays mentally:

```java
// Challenge 1
int[] arr1 = {5, 10, 15, 20, 25};
// Expected: [25, 20, 15, 10, 5]

// Challenge 2
int[] arr2 = {100, 200, 300};
// Expected: [300, 200, 100]

// Challenge 3
int[] arr3 = {1};
// Expected: [1]
```

---

**Master the two-pointer technique - it's used everywhere! 🎯**