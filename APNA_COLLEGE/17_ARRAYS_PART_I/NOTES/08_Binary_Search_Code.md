# 📚 Module: Arrays (Part - I) | Lecture 08: Binary Search Code

---

## 💻 Binary Search Implementation

### 🔧 Complete Code:

```java
public class BinarySearchCode {
    
    public static int binarySearch(int numbers[], int key) {
        
        // Initialize start and end pointers
        int start = 0;
        int end = numbers.length - 1;
        
        // Loop while search space is valid
        while(start <= end) {
            
            // Calculate middle index
            int mid = (start + end) / 2;
            
            // Case 1: Key found at middle
            if(numbers[mid] == key) {
                return mid;
            }
            
            // Case 2: Key is in right half
            else if(numbers[mid] < key) {
                start = mid + 1;
            }
            
            // Case 3: Key is in left half
            else {
                end = mid - 1;
            }
        }
        
        // Key not found in array
        return -1;
    }
    
    public static void main(String[] args) {
        
        // Create sorted array
        int numbers[] = {2, 4, 6, 8, 10, 12, 14};
        
        // Test Case 1: Key exists - 10
        int key = 10;
        int index = binarySearch(numbers, key);
        System.out.println("Index for key " + key + " is: " + index);
        
        // Test Case 2: Key exists - 4
        key = 4;
        index = binarySearch(numbers, key);
        System.out.println("Index for key " + key + " is: " + index);
        
        // Test Case 3: Key doesn't exist - 25
        key = 25;
        index = binarySearch(numbers, key);
        System.out.println("Index for key " + key + " is: " + index);
    }
}
```

### 📊 Output:
```
Index for key 10 is: 4
Index for key 4 is: 1
Index for key 25 is: -1
```

---

## 🔍 Understanding Each Step

### 📝 Function Parameters:

```java
public static int binarySearch(int numbers[], int key)
```

| Parameter | Purpose |
|---|---|
| `numbers[]` | The sorted array to search in |
| `key` | The element we're looking for |

---

### 🎯 Key Variables:

```java
int start = 0;                    // Left boundary
int end = numbers.length - 1;     // Right boundary
int mid = (start + end) / 2;      // Middle point
```

### ⚠️ Why `end = numbers.length - 1`?

```
Array indices: 0, 1, 2, 3, 4, 5, 6
Last valid index: 6
length: 7
end = 7 - 1 = 6 ✅ CORRECT

end = 7 ❌ WRONG (out of bounds!)
```

---

## 🧠 Loop Condition Explanation

### 📌 Why `start <= end`?

```java
while(start <= end)  // ✅ CORRECT
while(start < end)   // ❌ WRONG
```

**The difference matters!**

```
Single element case:
start = 4, end = 4

With start < end:     Loop doesn't run! ❌
With start <= end:    Loop runs, checks element ✅
```

---

## 📊 Three Comparison Cases

### Case 1️⃣: Key Found

```java
if(numbers[mid] == key) {
    return mid;  // Return immediately
}
```

**Example:**
```
Array: [2, 4, 6, 8, 10, 12, 14]
key = 10, mid = 3, numbers[3] = 8

8 == 10? NO → Continue
```

---

### Case 2️⃣: Key in Right Half

```java
else if(numbers[mid] < key) {
    start = mid + 1;  // Move start to right
}
```

**Logic:**
- If mid element is **smaller** than key
- Key must be **to the right**
- Search right half next

**Example:**
```
Array: [2, 4, 6, 8, 10, 12, 14]
key = 10, mid = 3, numbers[3] = 8

8 < 10? YES
start = 3 + 1 = 4 (search [10, 12, 14])
```

---

### Case 3️⃣: Key in Left Half

```java
else {
    end = mid - 1;  // Move end to left
}
```

**Logic:**
- If mid element is **larger** than key
- Key must be **to the left**
- Search left half next

**Example:**
```
Array: [2, 4, 6, 8, 10, 12, 14]
key = 10, mid = 5, numbers[5] = 12

12 > 10? YES
end = 5 - 1 = 4 (search [2, 4, 6, 8, 10])
```

---

## 🔄 Complete Step-by-Step Execution

### 🎯 Search for key=10 in `[2, 4, 6, 8, 10, 12, 14]`

```
Iteration 1:
start=0, end=6
mid = (0+6)/2 = 3
numbers[3] = 8
8 < 10? YES
start = 4

Iteration 2:
start=4, end=6
mid = (4+6)/2 = 5
numbers[5] = 12
12 > 10? YES
end = 4

Iteration 3:
start=4, end=4
mid = (4+4)/2 = 4
numbers[4] = 10
10 == 10? YES ✅
Return 4
```

---

## 🧪 Test Cases and Results

### ✅ Test Case 1: Key Exists in Array

```java
int numbers[] = {2, 4, 6, 8, 10, 12, 14};
int key = 10;
int index = binarySearch(numbers, key);
// Result: index = 4 ✅
```

### ✅ Test Case 2: Key at Different Position

```java
int numbers[] = {2, 4, 6, 8, 10, 12, 14};
int key = 4;
int index = binarySearch(numbers, key);
// Result: index = 1 ✅
```

### ❌ Test Case 3: Key Doesn't Exist

```java
int numbers[] = {2, 4, 6, 8, 10, 12, 14};
int key = 25;
int index = binarySearch(numbers, key);
// Result: index = -1 ❌ (not found)
```

**Why -1?**
- Valid indices: 0, 1, 2, 3, 4, 5, 6
- -1 is impossible index
- Convention: -1 means "not found"

---

## ⏱️ Time Complexity Analysis

### 📈 How Array Size Reduces Each Iteration:

```
Iteration 1: Array size = n       (Check 1 element)
Iteration 2: Array size = n/2     (Check 1 element)
Iteration 3: Array size = n/4     (Check 1 element)
Iteration 4: Array size = n/8     (Check 1 element)
...
Iteration k: Array size = n/2^k   (Check 1 element)

Until: n/2^k = 1
Therefore: 2^k = n
So: k = log₂(n)
```

### 🔍 Mathematical Derivation:

```
n/2^k = 1
n = 2^k
Taking log on both sides:
log₂(n) = k

Therefore: Time Complexity = O(log n)
```

---

## 📊 Comparison: Linear vs Binary Search

### 🎯 Array Size: n = 8 elements

```
Linear Search:
┌──────────────────────────────┐
│ Check all 8 elements         │
│ Worst case: 8 comparisons    │
│ Time Complexity: O(8)        │
└──────────────────────────────┘

Binary Search:
┌──────────────────────────────┐
│ Iteration 1: 8 → check 1     │
│ Iteration 2: 4 → check 1     │
│ Iteration 3: 2 → check 1     │
│ Iteration 4: 1 → check 1     │
│ Worst case: 4 comparisons    │
│ Time Complexity: O(log 8)=O(3)│
└──────────────────────────────┘

Binary Search: 2x faster! ⚡
```

---

### 🎯 Array Size: n = 1,000,000 elements

```
Linear Search:
Worst case: 1,000,000 comparisons
O(n) = O(1,000,000)

Binary Search:
log₂(1,000,000) ≈ 20 comparisons
O(log n) = O(20)

Binary Search: 50,000x faster! 🚀
```

---

## 📈 Complexity Graph

```
Time Complexity Comparison:

Operations
   |
   |  Linear: O(n)
   |  /
   | /
   |/ Binary: O(log n)
   |_______________
   0    100   1000   n (array size)

Binary Search stays flat!
Linear Search keeps growing!
```

---

## 🎨 Algorithm Flowchart

```
┌──────────────────────────────┐
│ Binary Search Start          │
│ start=0, end=length-1        │
└────────────┬─────────────────┘
             ↓
┌──────────────────────────────┐
│ start <= end?                │
└────┬──────────────────┬──────┘
    NO                 YES
     ↓                  ↓
Return -1      ┌────────────────┐
               │ mid=(s+e)/2    │
               └────────┬───────┘
                        ↓
          ┌─────────────────────────┐
          │ Compare arr[mid] & key  │
          └──┬────────┬────────┬────┘
           ==        <        >
            ↓        ↓        ↓
         Return    start   end
         mid       =mid+1  =mid-1
            ↓        ↓        ↓
          Found    Loop    Loop
                    ↓        ↓
                    └───┬────┘
                        ↓
                   Check condition
                   start <= end?
```

---

## 🎓 Key Implementation Points

### ⚠️ Important Details:

| Point | Detail |
|---|---|
| **Initialization** | `start = 0`, `end = length - 1` |
| **Mid Calculation** | `mid = (start + end) / 2` |
| **Loop Condition** | `while(start <= end)` |
| **Right Half** | `start = mid + 1` |
| **Left Half** | `end = mid - 1` |
| **Not Found** | `return -1` |

---

## 💻 Real-World Scenario

### 📕 Dictionary Search Analogy:

```
Searching for "Mango" in dictionary:

Traditional (Linear): A, B, C, D, ...M... (slow)
Binary Method:
1. Open to middle: G-H (too early)
2. Open later: T-U (too late)
3. Open between: L-O (found M!)

Time saved: Dramatically faster!
```

---

## 🎯 Why Binary Search is Better

### ✅ Advantages:

```
✅ Much faster for large datasets
✅ O(log n) vs O(n) complexity
✅ Predictable performance
✅ Scales well with size
```

### ❌ Constraints:

```
❌ Array must be SORTED
❌ Cannot search unsorted data
❌ Need to sort first if unsorted
```

---

## 📋 Comparison Table

### Linear vs Binary Search Code:

| Aspect | Linear | Binary |
|---|---|---|
| **Code lines** | ~5 | ~10 |
| **Loops** | 1 simple | 1 with mid-calc |
| **Requirement** | Any array | Sorted array |
| **Speed** | Slow (O(n)) | Fast (O(log n)) |
| **Best for** | Small arrays | Large arrays |
| **Ease** | Easier | Slightly complex |

---

## 🔑 Key Concepts from Lecture 08

✅ **Function takes array and key as parameters**  
✅ **Initialize start=0, end=length-1**  
✅ **Loop condition: start <= end** (includes equality)  
✅ **Calculate mid: (start + end) / 2**  
✅ **Three cases: Equal, Less than, Greater than**  
✅ **Move boundaries: start=mid+1 or end=mid-1**  
✅ **Return -1 if not found**  
✅ **Time Complexity: O(log n)**  
✅ **Always exponentially faster than Linear Search**  

---

## 🎯 When to Use Each Method

| Scenario | Use |
|---|---|
| Array < 100 elements | Either method |
| Array > 10,000 elements | **Binary (much faster)** |
| Need to search multiple times | Sort once, Binary search many |
| Array is unsorted | Linear or sort first |
| Don't know if sorted | Check or sort first |

---

## 📊 Performance Summary

```
Array Size    Linear Search    Binary Search    Speedup
─────────────────────────────────────────────────────
100           100              ~7              14x
1,000         1,000            ~10             100x
10,000        10,000           ~14             700x
1,000,000     1,000,000        ~20             50,000x

Binary Search dominates! 🚀
```

---

**Now you understand Binary Search completely! Ready for more algorithms! 🎯**