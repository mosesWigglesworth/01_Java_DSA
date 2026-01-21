# 📚 Module: Arrays (Part - I) | Lecture 06: Largest in Array

---

## 🎯 Problem: Find the Largest Number

### 💡 Real-World Example:

You have grades from multiple exams and need to find your **highest score**.

```
Scores: [1, 2, 6, 3, 5]

Need to find: 6 (the largest)
```

---

## 🔍 Algorithm: Finding Maximum Value

### 📝 Approach:

1. Initialize a variable with the **smallest possible value**
2. Compare each array element with this variable
3. If element is **larger**, update the variable
4. Return the final value

---

## 🧠 Step-by-Step Walkthrough

### 📊 Array: `[1, 2, 6, 3, 5]`

```
Step 1: Initialize largest = -∞ (Integer.MIN_VALUE)
        largest = -2147483648

Step 2: Compare 1 with largest
        1 > -∞? YES → largest = 1

Step 3: Compare 2 with largest
        2 > 1? YES → largest = 2

Step 4: Compare 6 with largest
        6 > 2? YES → largest = 6

Step 5: Compare 3 with largest
        3 > 6? NO → largest stays 6

Step 6: Compare 5 with largest
        5 > 6? NO → largest stays 6

Result: largest = 6 ✅
```

---

## 💻 Code Implementation

### 🔧 Java Infinity Constants:

| Constant | Represents | Value |
|---|---|---|
| `Integer.MIN_VALUE` | -∞ (negative infinity) | -2147483648 |
| `Integer.MAX_VALUE` | +∞ (positive infinity) | 2147483647 |

### 📝 Finding Largest:

```java
public class LargestNumber {
    
    public static int getLargest(int numbers[]) {
        
        // Initialize with smallest possible value
        int largest = Integer.MIN_VALUE;
        
        // Compare each element with largest
        for(int i = 0; i < numbers.length; i++) {
            if(numbers[i] > largest) {
                largest = numbers[i];
            }
        }
        
        // Return the largest value found
        return largest;
    }
    
    public static void main(String[] args) {
        
        // Create array
        int numbers[] = {1, 2, 6, 3, 5};
        
        // Call function and print result
        System.out.println("Largest value is: " + getLargest(numbers));
    }
}
```

### 📊 Output:
```
Largest value is: 6
```

---

## 🎯 Finding Smallest (Minimum)

### 🔧 Similar Approach - Opposite Logic:

```java
public class SmallestNumber {
    
    public static int getSmallest(int numbers[]) {
        
        // Initialize with largest possible value
        int smallest = Integer.MAX_VALUE;
        
        // Compare each element with smallest
        for(int i = 0; i < numbers.length; i++) {
            if(numbers[i] < smallest) {
                smallest = numbers[i];
            }
        }
        
        // Return the smallest value found
        return smallest;
    }
    
    public static void main(String[] args) {
        
        int numbers[] = {1, 2, 6, 3, 5};
        
        System.out.println("Smallest value is: " + getSmallest(numbers));
    }
}
```

### 📊 Output:
```
Smallest value is: 1
```

---

## 🎨 Complete Program: Both Largest and Smallest

### 💻 Full Code:

```java
public class MinMaxArray {
    
    public static int getLargest(int numbers[]) {
        int largest = Integer.MIN_VALUE;
        
        for(int i = 0; i < numbers.length; i++) {
            if(numbers[i] > largest) {
                largest = numbers[i];
            }
        }
        
        return largest;
    }
    
    public static int getSmallest(int numbers[]) {
        int smallest = Integer.MAX_VALUE;
        
        for(int i = 0; i < numbers.length; i++) {
            if(numbers[i] < smallest) {
                smallest = numbers[i];
            }
        }
        
        return smallest;
    }
    
    public static void main(String[] args) {
        
        int numbers[] = {1, 2, 6, 3, 5};
        
        System.out.println("Array: [1, 2, 6, 3, 5]");
        System.out.println("Largest value is: " + getLargest(numbers));
        System.out.println("Smallest value is: " + getSmallest(numbers));
    }
}
```

### 📊 Output:
```
Array: [1, 2, 6, 3, 5]
Largest value is: 6
Smallest value is: 1
```

---

## 🔑 Why Initialize with MIN_VALUE and MAX_VALUE?

### 💡 The Logic:

| Goal | Initialization | Why |
|---|---|---|
| **Find MAX** | `Integer.MIN_VALUE` | All array values > MIN_VALUE |
| **Find MIN** | `Integer.MAX_VALUE` | All array values < MAX_VALUE |

### 📊 Visual Explanation:

```
Finding Largest:
┌─────────────────────────────┐
│ largest = Integer.MIN_VALUE │
│ (very negative)             │
└──────────────┬──────────────┘
               ↓
        All array values
        will be larger
               ↓
     Will get updated correctly


Finding Smallest:
┌─────────────────────────────┐
│ smallest = Integer.MAX_VALUE│
│ (very positive)             │
└──────────────┬──────────────┘
               ↓
        All array values
        will be smaller
               ↓
     Will get updated correctly
```

---

## ⚠️ Why This Approach Works

### ❌ What Would Happen Without Proper Initialization?

```java
// WRONG: Start with first element
int largest = numbers[0];  // If array is [1, 2, 6, 3, 5]
                           // largest = 1
```

**Problem:** What if all numbers in array were **negative**?
```
Array: [-5, -3, -8, -2]
largest = numbers[0] = -5

But we need to check if -2 or -3 is larger!
This approach misses some elements.
```

**Solution:** Start with extreme value:
```java
int largest = Integer.MIN_VALUE;  // ✅ Works for all cases
                                  // Including all negative numbers
```

---

## 📊 Algorithm Comparison Table

### Finding Largest vs Smallest:

| Aspect | Largest | Smallest |
|---|---|---|
| **Initialize with** | `Integer.MIN_VALUE` | `Integer.MAX_VALUE` |
| **Condition** | `if(arr[i] > largest)` | `if(arr[i] < smallest)` |
| **Update** | `largest = arr[i]` | `smallest = arr[i]` |
| **Return** | `largest` | `smallest` |

---

## 🔁 Step-by-Step Code Execution

### 📍 Array: `[1, 2, 6, 3, 5]`

```
Initial: largest = -2147483648

i=0: numbers[0]=1
     1 > -2147483648? YES
     largest = 1

i=1: numbers[1]=2
     2 > 1? YES
     largest = 2

i=2: numbers[2]=6
     6 > 2? YES
     largest = 6

i=3: numbers[3]=3
     3 > 6? NO
     largest = 6 (no change)

i=4: numbers[4]=5
     5 > 6? NO
     largest = 6 (no change)

Loop ends: largest = 6 ✅
```

---

## 🧪 Different Test Cases

### ✅ Case 1: Normal Array
```java
int[] arr = {1, 2, 6, 3, 5};
// Largest: 6
// Smallest: 1
```

### ✅ Case 2: All Negative Numbers
```java
int[] arr = {-5, -3, -8, -2};
// Largest: -2
// Smallest: -8
```

### ✅ Case 3: Duplicate Values
```java
int[] arr = {5, 5, 5, 5};
// Largest: 5
// Smallest: 5
```

### ✅ Case 4: Single Element
```java
int[] arr = {42};
// Largest: 42
// Smallest: 42
```

---

## ⏱️ Time Complexity Analysis

### 🔍 Finding Largest/Smallest:

```
Loop: for(int i = 0; i < numbers.length; i++)
      
Iterations: n (where n = array length)

Work per iteration: 1 comparison and possible assignment

Total work: n comparisons

Time Complexity: O(n)
```

### 📈 Why O(n)?

```
Array size: 10 elements → 10 comparisons
Array size: 100 elements → 100 comparisons
Array size: 1000 elements → 1000 comparisons

Time grows linearly with array size
```

---

## 📋 Key Concepts from Lecture 06

✅ **Initialize largest with** `Integer.MIN_VALUE`  
✅ **Initialize smallest with** `Integer.MAX_VALUE`  
✅ Compare each element with current max/min  
✅ Update when a larger/smaller value is found  
✅ **Time Complexity:** O(n) - single pass through array  
✅ Works for negative numbers, duplicates, and all edge cases  

---

## 🎨 Visual Algorithm Flow

```
┌─────────────────────────────────┐
│ Initialize largest = MIN_VALUE  │
└────────────┬────────────────────┘
             ↓
┌─────────────────────────────────┐
│ Loop through each array element │
│ (i = 0 to length-1)            │
└────────────┬────────────────────┘
             ↓
┌─────────────────────────────────┐
│ Is arr[i] > largest?           │
└────┬──────────────────────┬─────┘
    YES                     NO
     ↓                       ↓
Update largest         No change
    ↓                       ↓
     └───────────┬──────────┘
                 ↓
        Continue to next element
                 ↓
        ┌─────────────────┐
        │ Loop complete?  │
        └────┬──────┬─────┘
            YES     NO
             ↓       ↓
          Return  Continue
          largest  loop
```

---

## 🎯 Common Mistakes to Avoid

### ❌ Mistake 1: Wrong Initialization
```java
int largest = 0;  // ❌ What if all numbers are negative?
int largest = Integer.MIN_VALUE;  // ✅ Correct
```

### ❌ Mistake 2: Wrong Comparison Operator
```java
if(numbers[i] < largest)  // ❌ Wrong for finding max
if(numbers[i] > largest)  // ✅ Correct for max
```

### ❌ Mistake 3: Not Updating Inside Loop
```java
for(int i = 0; i < n; i++) {
    // Missing: largest = numbers[i];
}  // ❌ Won't update
```

---

## 💡 Real-World Applications

| Application | Use Case |
|---|---|
| **Grades** | Find highest score |
| **Temperatures** | Find hottest/coldest day |
| **Sales** | Find best/worst performing product |
| **Performance** | Find fastest/slowest time |
| **Inventory** | Find maximum/minimum stock |

---

**Ready for more complex array operations! 🚀**

Similar code found with 1 license type