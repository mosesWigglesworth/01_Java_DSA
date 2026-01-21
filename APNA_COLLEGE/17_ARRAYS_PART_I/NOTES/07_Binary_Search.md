# 📚 Module: Arrays (Part - I) | Lecture 07: Binary Search

---

## 🎯 What is Binary Search?

### 💡 Real-World Example: Dictionary Search

Imagine finding a word in a **dictionary**:

```
Dictionary (Sorted):
Apple
Banana
Chickoo
Litchi
Mango
Strawberry
```

**Don't you start from 'A'?** ❌

You know "Mango" starts with 'M', so you:
1. Open dictionary roughly in the **middle**
2. Check if you're at M section
3. If too early → jump forward
4. If too late → jump backward
5. Repeat until found

**This is Binary Search!** ✅

---

## 🔍 Binary Search Definition

> **Binary Search:** A fast searching technique that works on **sorted arrays** by repeatedly dividing the search space in half.

### 📌 Key Requirements:

| Requirement | Details |
|---|---|
| **Array Type** | **Must be SORTED** |
| **Sort Order** | Increasing (2,4,6,8...) or Decreasing (8,7,6,5...) |
| **Speed** | Much faster than Linear Search |
| **Complexity** | O(log n) - logarithmic |

---

## 📊 Binary Search Step-by-Step Example

### 🎯 Problem:
Search for **key = 10** in sorted array: `[2, 4, 6, 8, 10, 12, 14]`

### 🔎 Search Process:

```
Initial Setup:
┌────────────────────────────────┐
│ Array: [2, 4, 6, 8, 10, 12, 14]│
│ start = 0,  end = 6             │
└────────────────────────────────┘

Step 1: Calculate mid
        mid = (0 + 6) / 2 = 3
        arr[3] = 8
        
        Is 8 == 10? NO
        Is 8 < 10? YES → Search right half
        start = mid + 1 = 4

Step 2: Calculate mid
        mid = (4 + 6) / 2 = 5
        arr[5] = 12
        
        Is 12 == 10? NO
        Is 12 > 10? YES → Search left half
        end = mid - 1 = 4

Step 3: Calculate mid
        mid = (4 + 4) / 2 = 4
        arr[4] = 10
        
        Is 10 == 10? YES ✅
        Found at index 4!
```

---

## 💻 Binary Search Code

### 🔧 Implementation:

```java
public class BinarySearch {
    
    public static int binarySearch(int arr[], int key) {
        
        int start = 0;
        int end = arr.length - 1;
        
        // Continue searching while search space is valid
        while(start <= end) {
            
            // Calculate middle index
            int mid = (start + end) / 2;
            
            // Compare middle element with key
            if(arr[mid] == key) {
                return mid;  // Found!
            }
            else if(arr[mid] < key) {
                // Key is in right half
                start = mid + 1;
            }
            else {
                // Key is in left half
                end = mid - 1;
            }
        }
        
        // Key not found
        return -1;
    }
    
    public static void main(String[] args) {
        
        int arr[] = {2, 4, 6, 8, 10, 12, 14};
        int key = 10;
        
        int result = binarySearch(arr, key);
        
        if(result == -1) {
            System.out.println("Key not found!");
        } else {
            System.out.println("Key found at index: " + result);
        }
    }
}
```

### 📊 Output:
```
Key found at index: 4
```

---

## 🧠 Binary Search Algorithm (Pseudocode)

### 📝 Step-by-Step Logic:

```
1. Initialize:
   start = 0
   end = array.length - 1

2. While loop: while(start <= end)
   
   a) Calculate mid = (start + end) / 2
   
   b) Compare arr[mid] with key:
      
      IF arr[mid] == key:
         RETURN mid (found!)
      
      ELSE IF arr[mid] < key:
         start = mid + 1  (search right half)
      
      ELSE:
         end = mid - 1    (search left half)

3. If loop ends without finding:
   RETURN -1 (not found)
```

---

## 🎨 Visual Binary Search Process

### 📊 Array: `[2, 4, 6, 8, 10, 12, 14]` searching for 10

```
Initial state:
start=0                          end=6
│                                │
▼                                ▼
[2, 4, 6, 8, 10, 12, 14]
           mid=3(8)
           8 < 10? YES → move right

Iteration 1:
start=4                    end=6
│                          │
▼                          ▼
         [10, 12, 14]
             mid=5(12)
             12 > 10? YES → move left

Iteration 2:
start=4, end=4
│
▼
[10]
mid=4(10)
10 == 10? YES ✅ Found!
```

---

## 📈 Key Points About Binary Search

### ⚠️ IMPORTANT: Array Must Be Sorted!

```java
// ✅ CORRECT - Sorted array
int arr[] = {2, 4, 6, 8, 10, 12, 14};
binarySearch(arr, 10);  // Works perfectly

// ❌ WRONG - Unsorted array
int arr[] = {10, 2, 14, 4, 8, 6, 12};
binarySearch(arr, 10);  // WILL NOT WORK!
```

### 📋 Why end = length - 1?

```java
int start = 0;           // First index
int end = arr.length - 1;  // Last index (NOT arr.length!)

// Example with 7 elements:
// Valid indices: 0, 1, 2, 3, 4, 5, 6
// end should be 6, NOT 7
```

---

## 🧪 Different Test Cases

### ✅ Case 1: Key Found in Middle

```java
int arr[] = {2, 4, 6, 8, 10, 12, 14};
int key = 8;

Result: Found at index 3
```

### ✅ Case 2: Key Found at End

```java
int arr[] = {2, 4, 6, 8, 10, 12, 14};
int key = 14;

Result: Found at index 6
```

### ✅ Case 3: Key Found at Start

```java
int arr[] = {2, 4, 6, 8, 10, 12, 14};
int key = 2;

Result: Found at index 0
```

### ❌ Case 4: Key Not Found

```java
int arr[] = {2, 4, 6, 8, 10, 12, 14};
int key = 99;

Result: -1 (Not found)
```

---

## ⏱️ Time Complexity Analysis

### 🔍 Binary Search vs Linear Search:

| Iteration | Array Size | Operations |
|---|---|---|
| Initial | n | 1 comparison |
| After 1st | n/2 | 1 comparison |
| After 2nd | n/4 | 1 comparison |
| After 3rd | n/8 | 1 comparison |
| ... | ... | ... |
| Final | 1 | 1 comparison |

### 📊 Complexity Calculation:

```
For array of size n:
- Linear Search: O(n) - must check all elements
- Binary Search: O(log n) - divide by 2 each time

Example: n = 1,000,000
- Linear: 1,000,000 comparisons (worst case)
- Binary: ~20 comparisons (log₂ 1,000,000 ≈ 20)

Binary Search is ~50,000 times faster!
```

### 📈 Why O(log n)?

```
Binary search keeps halving the array:
n → n/2 → n/4 → n/8 → ... → 1

How many times can you divide n by 2?
Answer: log₂(n) times

That's why time complexity is O(log n)
```

---

## 🎯 Complete Program with Multiple Cases

### 💻 Full Implementation:

```java
public class BinarySearchDemo {
    
    public static int binarySearch(int arr[], int key) {
        
        int start = 0;
        int end = arr.length - 1;
        
        while(start <= end) {
            
            int mid = (start + end) / 2;
            
            System.out.println("Checking: start=" + start + 
                             ", mid=" + mid + ", end=" + end + 
                             ", arr[mid]=" + arr[mid]);
            
            if(arr[mid] == key) {
                return mid;
            }
            else if(arr[mid] < key) {
                start = mid + 1;
            }
            else {
                end = mid - 1;
            }
        }
        
        return -1;
    }
    
    public static void main(String[] args) {
        
        int arr[] = {2, 4, 6, 8, 10, 12, 14};
        
        // Test Case 1: Key found
        System.out.println("Searching for 10:");
        int result = binarySearch(arr, 10);
        System.out.println("Result: " + (result == -1 ? "Not found" : 
                          "Found at index " + result));
        
        System.out.println("\nSearching for 99:");
        result = binarySearch(arr, 99);
        System.out.println("Result: " + (result == -1 ? "Not found" : 
                          "Found at index " + result));
    }
}
```

---

## 🔄 Comparing Search Methods

### 📊 Linear vs Binary Search:

| Aspect | Linear Search | Binary Search |
|---|---|---|
| **Requirement** | Any array | Sorted array only |
| **Time Complexity** | O(n) | O(log n) |
| **Worst Case** | Check all n elements | ~log₂(n) comparisons |
| **Speed** | Slower for large data | Much faster |
| **Use Case** | Small/unsorted arrays | Large sorted data |
| **Implementation** | Simple | Bit complex |

---

## 🎨 Visual Algorithm Flow

```
┌──────────────────────────┐
│ Binary Search Start      │
│ start=0, end=n-1         │
└───────────┬──────────────┘
            ↓
┌──────────────────────────┐
│ start <= end?            │
└──┬─────────────────┬─────┘
  NO                YES
   ↓                 ↓
Return -1    ┌──────────────┐
             │ mid=(s+e)/2  │
             └──────┬───────┘
                    ↓
          ┌─────────────────────┐
          │ arr[mid] == key?    │
          └──┬────────┬────────┬─┘
            YES      <        >
             ↓       ↓        ↓
          Return   start  end
           mid    =mid+1 =mid-1
             ↓       ↓        ↓
          Found    Loop    Loop
```

---

## ⚠️ Common Mistakes to Avoid

### ❌ Mistake 1: Forgetting Array Must Be Sorted
```java
int arr[] = {5, 2, 8, 1, 9};  // ❌ Unsorted
binarySearch(arr, 8);          // WRONG RESULT!
```

### ❌ Mistake 2: Wrong End Initialization
```java
int end = arr.length;  // ❌ WRONG - Out of bounds
int end = arr.length - 1;  // ✅ CORRECT
```

### ❌ Mistake 3: Wrong Mid Calculation
```java
int mid = (start + end) / 2;  // ✅ CORRECT
int mid = start + end / 2;    // ❌ WRONG (operator precedence)
```

### ❌ Mistake 4: Wrong Loop Condition
```java
while(start < end)  // ❌ Might miss single element
while(start <= end)  // ✅ CORRECT
```

---

## 💡 When to Use Binary Search?

| Scenario | Use Binary? |
|---|---|
| **Sorted array, need to find element** | ✅ YES - O(log n) |
| **Unsorted array** | ❌ NO - Need to sort first |
| **Array < 100 elements** | ❓ Either method works |
| **Array > 10,000 elements** | ✅ YES - Much faster |
| **Frequently searching** | ✅ YES - Sort once, search many times |

---

## 🔑 Key Concepts from Lecture 07

✅ **Binary Search requires SORTED array**  
✅ **Divides search space by 2 each iteration**  
✅ **Time Complexity: O(log n)** - Much faster than O(n)  
✅ **Initialize:** start=0, end=length-1  
✅ **Mid formula:** mid = (start + end) / 2  
✅ **Three cases:** Equal, Less than, Greater than  
✅ **Return -1 if not found** (like Linear Search)  
✅ **Compare with dictionary search** for intuition  

---

## 📈 Performance Comparison Example

```
Array size: 1,000,000 elements
Searching for element at worst case:

Linear Search:    1,000,000 comparisons
Binary Search:    ~20 comparisons

Speed improvement: 50,000x faster! 🚀
```

---

**Ready for more advanced array problems! 🎯**