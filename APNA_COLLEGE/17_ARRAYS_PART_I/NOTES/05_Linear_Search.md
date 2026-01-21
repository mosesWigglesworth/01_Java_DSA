# 📚 Module: Arrays (Part - I) | Lecture 05: Linear Search

---

## 🎯 What is Linear Search?

### 💡 Real-World Example:

Imagine you're at a college canteen looking for **samosas** in the menu:

```
Menu Items:
1. Dosa         ❌ Not samosa
2. Chole Bhature ❌ Not samosa
3. Samosa       ✅ Found it!
4. Sandwich
5. Coke
```

You scan **one by one** from top to bottom until you find what you need.

**This is Linear Search!**

---

## 🔍 Linear Search Definition

> **Linear Search:** A technique to find a specific element in an array by checking each element sequentially from the beginning until the element is found or the array ends.

### 📌 Key Characteristics:

| Aspect | Detail |
|---|---|
| **Method** | Check one element at a time |
| **Direction** | From first to last index |
| **Stop Condition** | When element found or array ends |
| **Simplicity** | Very simple and straightforward |

---

## 📊 Linear Search Example

### 🎯 Problem:
Find index of key **10** in array: `[2, 4, 6, 8, 10, 12, 14, 16]`

### 🔎 Search Process:

```
Index 0: Is 2 == 10?  ❌ NO
Index 1: Is 4 == 10?  ❌ NO
Index 2: Is 6 == 10?  ❌ NO
Index 3: Is 8 == 10?  ❌ NO
Index 4: Is 10 == 10? ✅ YES → Return 4
```

**Result:** Key found at **Index 4**

---

## 💻 Linear Search Code

### 🔧 Function Implementation:

```java
public static int linearSearch(int numbers[], int key) {
    
    // Loop through all array indices
    for(int i = 0; i < numbers.length; i++) {
        
        // Check if current element equals key
        if(numbers[i] == key) {
            return i;  // Found! Return index
        }
    }
    
    // Key not found in array
    return -1;  // Return -1 to indicate not found
}
```

### 🔑 Key Points:

| Component | Purpose |
|---|---|
| **Loop** | `for(int i = 0; i < numbers.length; i++)` |
| **Condition** | `if(numbers[i] == key)` |
| **Success** | `return i;` (return found index) |
| **Failure** | `return -1;` (element doesn't exist) |

---

## 📝 Complete Program Example

### 💻 Full Code:

```java
public class LinearSearch {
    
    // Linear search function
    public static int linearSearch(int numbers[], int key) {
        
        for(int i = 0; i < numbers.length; i++) {
            if(numbers[i] == key) {
                return i;  // Found at index i
            }
        }
        
        return -1;  // Not found
    }
    
    public static void main(String[] args) {
        
        // Create array
        int numbers[] = {2, 4, 6, 8, 10, 12, 14, 16};
        
        // Define key to search
        int key = 10;
        
        // Call linear search function
        int index = linearSearch(numbers, key);
        
        // Check result
        if(index == -1) {
            System.out.println("Key not found!");
        } else {
            System.out.println("Key is at index: " + index);
        }
    }
}
```

### 📊 Output:
```
Key is at index: 4
```

---

## 🧪 Testing Different Cases

### ✅ Case 1: Key Found

```java
int numbers[] = {2, 4, 6, 8, 10, 12, 14, 16};
int key = 10;

// Result: Found at index 4
```

### ❌ Case 2: Key Not Found

```java
int numbers[] = {2, 4, 6, 8, 10, 12, 14, 16};
int key = 20;  // 20 doesn't exist in array

// Result: -1 (Not found)
System.out.println("Key not found!");
```

---

## 🎯 Return Value Convention

| Return Value | Meaning |
|---|---|
| **0 to n-1** | ✅ Key found at this index |
| **-1** | ❌ Key not found anywhere |

**Why -1?**
- Indices range from 0 to length-1
- -1 is impossible index → indicates "not found"

---

## 🔄 Linear Search Step-by-Step Walkthrough

### 📍 Array: `[2, 4, 6, 8, 10, 12, 14, 16]`
### 🔑 Searching for: `10`

```
Step 1: i=0, numbers[0]=2
        Compare: 2 == 10? NO → Continue

Step 2: i=1, numbers[1]=4
        Compare: 4 == 10? NO → Continue

Step 3: i=2, numbers[2]=6
        Compare: 6 == 10? NO → Continue

Step 4: i=3, numbers[3]=8
        Compare: 8 == 10? NO → Continue

Step 5: i=4, numbers[4]=10
        Compare: 10 == 10? YES → Return 4 ✅
```

---

## 🧵 Linear Search with String Arrays

### 💡 Real-World Example: Menu Search

```java
public class MenuSearch {
    
    public static int linearSearch(String menu[], String item) {
        for(int i = 0; i < menu.length; i++) {
            if(menu[i].equals(item)) {  // Use .equals() for strings
                return i;
            }
        }
        return -1;
    }
    
    public static void main(String[] args) {
        
        String menu[] = {"Dosa", "Chole Bhature", "Samosa", 
                         "Sandwich", "Coke"};
        
        String searchItem = "Samosa";
        
        int index = linearSearch(menu, searchItem);
        
        if(index == -1) {
            System.out.println("Item not in menu!");
        } else {
            System.out.println(searchItem + " found at index: " + index);
        }
    }
}
```

### 📊 Output:
```
Samosa found at index: 2
```

### ⚠️ Important Note:
```java
// For strings, use .equals() not ==
if(menu[i].equals(item))  // ✅ Correct
if(menu[i] == item)       // ❌ May not work (compares references)
```

---

## ⏱️ Time Complexity Analysis

### 🔍 Understanding Time Complexity:

**Time Complexity** tells us how long a program takes to run relative to input size.

### 📊 Linear Search Time Complexity:

```
Best Case:    O(1)    → Element found at index 0 (1 comparison)
Average Case: O(n/2)  → Element found in middle (n/2 comparisons)
Worst Case:   O(n)    → Element not found or at last index (n comparisons)
```

### 📈 Why Linear Search is O(n):

```
Loop runs:    for(int i = 0; i < n; i++)
Iterations:   n times (where n = array length)
Work per iteration: 1 comparison

Total work:   n comparisons → O(n)
```

### 💡 Explanation:

```
Array size: 8 elements
Search for: 20 (not found)

Comparisons needed: 8 (check all elements)
Time complexity: O(n) where n = 8

Array size: 100 elements
Search for: key not found

Comparisons needed: 100
Time complexity: O(n) where n = 100

Conclusion: Time grows proportionally with array size
```

---

## 📋 Linear Search Algorithm Summary

### 🎯 Algorithm Steps:

```
1. Start from first index (i = 0)
2. Check if current element equals key
   - If YES → Return current index
   - If NO → Continue to next
3. Move to next index (i++)
4. Repeat steps 2-3 until array ends
5. If array ends without finding key → Return -1
```

### 🖼️ Visual Flow:

```
┌─────────────────────┐
│ Start Linear Search │
└──────────┬──────────┘
           ↓
┌─────────────────────────┐
│ i = 0, check arr[i]     │
└──────────┬──────────────┘
           ↓
    ┌──────────────┐
    │ arr[i]==key? │
    └──┬───────┬───┘
     YES       NO
      ↓         ↓
   Return    i++, loop
    Index    again
      ↓
   ┌─────────────┐
   │ End reached?│
   └──┬────────┬─┘
     YES       NO
      ↓         ↓
   Return   Continue
    -1      Search
```

---

## 🎓 Key Concepts from Lecture 05

✅ **Linear Search** scans array sequentially  
✅ Check one element at a time until found  
✅ Return **index** if found, **-1** if not found  
✅ Use `==` for integers, `.equals()` for strings  
✅ **Time Complexity:** O(n) - proportional to array size  
✅ **Worst Case:** Must check all elements  
✅ Simple but may be slow for large arrays  

---

## 📝 Homework Challenge

Create a linear search for a String array menu:

```java
String menu[] = {"Dosa", "Chole Bhature", "Samosa", 
                 "Sandwich", "Coke"};

// Search for different items
// Use string comparison with .equals()
```

---

**Ready for Binary Search - a faster alternative! 🚀**