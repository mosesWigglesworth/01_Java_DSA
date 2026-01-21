# 📚 Module: Arrays (Part - I) | Lecture 11: Print Subarray

---

## 🎯 Problem: Print All Subarrays

### 💡 What is a Subarray?

A **subarray** is a **contiguous** part of an array:

```
Original Array: [2, 4, 6, 8, 10]

Valid Subarrays:
[2]
[2, 4]
[2, 4, 6]
[4, 6]
[6, 8, 10]
etc.

Invalid (NOT contiguous):
[2, 6, 10]  ❌ (missing 4 and 8)
[2, 8]      ❌ (missing 4 and 6)
```

**Key Rule:** Elements must be consecutive/adjacent in the original array

---

## 📊 All Subarrays Example

### 🎯 Array: `[2, 4, 6, 8, 10]`

```
Subarrays starting with 2:
[2]
[2, 4]
[2, 4, 6]
[2, 4, 6, 8]
[2, 4, 6, 8, 10]
→ 5 subarrays

Subarrays starting with 4:
[4]
[4, 6]
[4, 6, 8]
[4, 6, 8, 10]
→ 4 subarrays

Subarrays starting with 6:
[6]
[6, 8]
[6, 8, 10]
→ 3 subarrays

Subarrays starting with 8:
[8]
[8, 10]
→ 2 subarrays

Subarrays starting with 10:
[10]
→ 1 subarray

Total: 5 + 4 + 3 + 2 + 1 = 15 subarrays
```

---

## 🧠 Understanding the Pattern

### 📈 Count of Subarrays:

```
For n elements:
Element 1: pairs with n elements = n subarrays
Element 2: pairs with (n-1) elements = (n-1) subarrays
Element 3: pairs with (n-2) elements = (n-2) subarrays
...
Element n: pairs with 1 element = 1 subarray

Total = n + (n-1) + (n-2) + ... + 1
      = n × (n+1) / 2
```

---

## 💻 Three Nested Loops Solution

### 🔑 The Algorithm:

```
Loop 1: Start point (i from 0 to n-1)
Loop 2: End point (j from i to n-1)
Loop 3: Print elements (k from i to j)
```

### 🔧 Code Structure:

```java
for(int i = 0; i < n; i++) {           // Loop 1: START
    for(int j = i; j < n; j++) {       // Loop 2: END
        for(int k = i; k <= j; k++) {  // Loop 3: PRINT
            System.out.print(arr[k] + " ");
        }
        System.out.println();
    }
}
```

---

## 💻 Complete Implementation

### 🔧 Full Program:

```java
public class PrintSubarrays {
    
    public static void printSubarrays(int numbers[]) {
        
        int totalSubarrays = 0;
        
        // Loop 1: Start point of subarray
        for(int i = 0; i < numbers.length; i++) {
            
            // Loop 2: End point of subarray
            for(int j = i; j < numbers.length; j++) {
                
                // Loop 3: Print elements from i to j
                for(int k = i; k <= j; k++) {
                    System.out.print(numbers[k] + " ");
                }
                
                System.out.println();
                totalSubarrays++;
            }
        }
        
        System.out.println("\nTotal subarrays: " + totalSubarrays);
    }
    
    public static void main(String[] args) {
        
        int numbers[] = {2, 4, 6, 8, 10};
        
        System.out.println("Array: [2, 4, 6, 8, 10]\n");
        System.out.println("All subarrays:");
        printSubarrays(numbers);
    }
}
```

### 📊 Output:
```
Array: [2, 4, 6, 8, 10]

All subarrays:
2 
2 4 
2 4 6 
2 4 6 8 
2 4 6 8 10 
4 
4 6 
4 6 8 
4 6 8 10 
6 
6 8 
6 8 10 
8 
8 10 
10 

Total subarrays: 15
```

---

## 🎨 Visual Execution Trace

### 📍 Array: `[2, 4, 6, 8, 10]` (indices 0-4)

```
i=0 (Start at 2):
  j=0: k=0 → [2]
  j=1: k=0,1 → [2,4]
  j=2: k=0,1,2 → [2,4,6]
  j=3: k=0,1,2,3 → [2,4,6,8]
  j=4: k=0,1,2,3,4 → [2,4,6,8,10]

i=1 (Start at 4):
  j=1: k=1 → [4]
  j=2: k=1,2 → [4,6]
  j=3: k=1,2,3 → [4,6,8]
  j=4: k=1,2,3,4 → [4,6,8,10]

i=2 (Start at 6):
  j=2: k=2 → [6]
  j=3: k=2,3 → [6,8]
  j=4: k=2,3,4 → [6,8,10]

i=3 (Start at 8):
  j=3: k=3 → [8]
  j=4: k=3,4 → [8,10]

i=4 (Start at 10):
  j=4: k=4 → [10]
```

---

## 🔑 Why Three Loops?

### 📋 Purpose of Each Loop:

| Loop | Purpose | Range |
|---|---|---|
| **Loop 1 (i)** | Define START point | 0 to n-1 |
| **Loop 2 (j)** | Define END point | i to n-1 |
| **Loop 3 (k)** | Print elements | i to j |

### 💡 Why `j = i` and NOT `j = i+1`?

```java
for(int j = i; j < n; j++)      // ✅ CORRECT
// Includes single element subarrays like [2], [4], [6]

for(int j = i+1; j < n; j++)    // ❌ WRONG
// Would skip single element subarrays
```

---

## 📈 Total Subarrays Formula

### 🔍 Mathematical Derivation:

```
For n elements:
Subarrays = 1 + 2 + 3 + ... + n
          = n × (n + 1) / 2
```

### 🎯 Examples:

```
n=5: TS = 5 × 6 / 2 = 15 ✅
n=4: TS = 4 × 5 / 2 = 10
n=3: TS = 3 × 4 / 2 = 6
n=2: TS = 2 × 3 / 2 = 3
n=1: TS = 1 × 2 / 2 = 1
```

---

## 💻 Program with Formula

### 🔧 Using Total Subarrays Formula:

```java
public class SubarraysFormula {
    
    public static void printSubarrays(int numbers[]) {
        
        System.out.println("All subarrays:");
        int totalSubarrays = 0;
        
        for(int i = 0; i < numbers.length; i++) {
            for(int j = i; j < numbers.length; j++) {
                for(int k = i; k <= j; k++) {
                    System.out.print(numbers[k] + " ");
                }
                System.out.println();
                totalSubarrays++;
            }
        }
        
        System.out.println("\nUsing loop count: " + totalSubarrays);
        
        // Using formula
        int n = numbers.length;
        int formulaTotal = n * (n + 1) / 2;
        System.out.println("Using formula: " + formulaTotal);
    }
    
    public static void main(String[] args) {
        
        int numbers[] = {2, 4, 6, 8, 10};
        
        System.out.println("Array: [2, 4, 6, 8, 10]");
        System.out.println("n = " + numbers.length + "\n");
        
        printSubarrays(numbers);
    }
}
```

---

## 🧪 Test Cases

### ✅ Test Case 1: Size 4

```java
int[] arr = {1, 2, 3, 4};
// Total subarrays = 4 × 5 / 2 = 10

Subarrays:
[1] [1,2] [1,2,3] [1,2,3,4]
[2] [2,3] [2,3,4]
[3] [3,4]
[4]
```

### ✅ Test Case 2: Size 3

```java
int[] arr = {10, 20, 30};
// Total subarrays = 3 × 4 / 2 = 6

Subarrays:
[10] [10,20] [10,20,30]
[20] [20,30]
[30]
```

### ✅ Test Case 3: Size 2

```java
int[] arr = {5, 10};
// Total subarrays = 2 × 3 / 2 = 3

Subarrays:
[5] [5,10]
[10]
```

---

## ⏱️ Time Complexity Analysis

### 🔍 Three Nested Loops:

```
Loop 1 (i): runs n times
Loop 2 (j): runs n, n-1, n-2, ... times
Loop 3 (k): runs 1, 2, 3, ... times

Total iterations:
= n × (n-1)/2 × (average length)
= n × (n+1)/2 × (n+2)/6
= O(n³)

For n=10: ~500 operations
For n=100: ~500,000 operations
```

### 📊 Complexity Graph:

```
Operations
    |
1000|          O(n³)
    |        /
 500|      /
    |    /
    |  /
    |________________
    0  5  10  15  n
```

---

## 🎨 Algorithm Flowchart

```
┌──────────────────────────────────┐
│ Loop 1: i from 0 to n-1         │
│ (Define START of subarray)       │
└────────────┬─────────────────────┘
             ↓
┌──────────────────────────────────┐
│ Loop 2: j from i to n-1         │
│ (Define END of subarray)         │
└────────────┬─────────────────────┘
             ↓
┌──────────────────────────────────┐
│ Loop 3: k from i to j           │
│ (Print elements in subarray)     │
└────────────┬─────────────────────┘
             ↓
┌──────────────────────────────────┐
│ Print arr[k]                     │
└────────────┬─────────────────────┘
             ↓
┌──────────────────────────────────┐
│ k++                              │
│ More elements? (k <= j)          │
└────┬──────────────────────┬──────┘
    YES                     NO
     ↓                       ↓
  Loop 3          ┌──────────────────┐
             │ Print newline       │
             │ totalSubarrays++    │
             └────────┬─────────────┘
                      ↓
             ┌──────────────────┐
             │ j++              │
             │ More ends? (j<n) │
             └────┬─────────┬───┘
                YES         NO
                 ↓           ↓
             Loop 2   ┌──────────────┐
                     │ i++          │
                     │ More starts? │
                     └──┬────────┬──┘
                      YES        NO
                       ↓          ↓
                    Loop 1    Complete
```

---

## 📋 Key Differences: Pairs vs Subarrays

| Aspect | Pairs | Subarrays |
|---|---|---|
| **Definition** | Any 2 elements | Contiguous elements |
| **Order** | (a,b) = (b,a) | Must be consecutive |
| **Loops** | 2 nested loops | 3 nested loops |
| **Loop 2 start** | j = i+1 | j = i |
| **Total formula** | n×(n-1)/2 | n×(n+1)/2 |
| **Time Complexity** | O(n²) | O(n³) |

---

## 🎯 Important Concepts

### ✅ Key Points:

```
1. Three nested loops required
   - Loop 1: Start point (i)
   - Loop 2: End point (j)
   - Loop 3: Print elements (k)

2. Why j = i (not i+1)?
   - To include single-element subarrays
   - [2] is a valid subarray

3. Total subarrays = n × (n+1) / 2

4. Contiguity is essential
   - Must be consecutive elements
   - No gaps allowed

5. Time Complexity: O(n³)
   - Three nested loops
   - Much slower than pairs O(n²)
```

---

## 💡 Homework Challenge

### 🎯 Problem: Find Min and Max Subarray Sum

**Task:** For all subarrays, calculate:
1. Sum of each subarray
2. Find **minimum** sum
3. Find **maximum** sum

### 📊 Example:

```
Array: [2, 4, 6, 8, 10]

Subarray [2]: sum = 2
Subarray [2,4]: sum = 6
Subarray [2,4,6]: sum = 12
Subarray [4,6]: sum = 10
Subarray [6,8,10]: sum = 24
...

Find:
- Minimum subarray sum
- Maximum subarray sum
```

### 💻 Hints:

```java
// Add this to the third loop:
int subarraySum = 0;
for(int k = i; k <= j; k++) {
    subarraySum += numbers[k];
}

// Track min and max:
minSum = Math.min(minSum, subarraySum);
maxSum = Math.max(maxSum, subarraySum);
```

---

## 🔑 Key Concepts from Lecture 11

✅ **Subarray = Contiguous part of array**  
✅ **Three nested loops required**  
✅ **Loop 1: Start point (i)**  
✅ **Loop 2: End point (j)**  
✅ **Loop 3: Print elements (k)**  
✅ **j = i** to include single-element subarrays  
✅ **Total subarrays formula: n×(n+1)/2**  
✅ **Time Complexity: O(n³)**  
✅ **Contiguity is mandatory**  

---

## 📝 Comparison Table

| Concept | Details |
|---|---|
| **Array** | [2, 4, 6, 8, 10] |
| **Subarray** | Contiguous subset |
| **Example Valid** | [2,4,6], [8,10], [6] |
| **Example Invalid** | [2,6,10], [2,8] |
| **Total for n=5** | 15 |
| **Formula** | n(n+1)/2 |
| **Loops** | 3 nested |
| **Time** | O(n³) |

---

## 🎓 Why This Matters

✅ **Foundation for subarray problems**  
✅ **Used in sum/product/max problems**  
✅ **Interview favorite**  
✅ **Tests understanding of nested loops**  
✅ **Builds strong logic foundation**  

---

**Complete the homework challenge to master subarrays! 🎯**