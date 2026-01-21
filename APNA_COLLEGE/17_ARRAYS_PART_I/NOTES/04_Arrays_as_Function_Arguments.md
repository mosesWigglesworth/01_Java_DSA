# 📚 Module: Arrays (Part - I) | Lecture 04: Arrays as Function Arguments

---

## 🎯 Pass by Value vs Pass by Reference

### 📌 Two Ways to Pass Variables to Functions:

| Method | What Happens | Changes Reflect? |
|---|---|---|
| **Pass by Value** | Copy of value is sent | ❌ NO (only in function) |
| **Pass by Reference** | Reference to original is sent | ✅ YES (in main function too) |

**🔑 Important:** Arrays are **ALWAYS passed by reference!**

---

## 🔗 Arrays: Pass by Reference

### 💡 What This Means:

When you pass an array to a function:
- The function gets access to the **original array in memory**
- Any changes made in the function **reflect in the calling function**
- It's like giving the address of your house instead of a copy

### 📊 Visual Comparison:

```
Pass by Value (Regular Variables):
┌─────────────┐
│ Main Fn     │
│ x = 5       │
└─────────────┘
        ↓ (copies value)
┌─────────────┐
│ Function    │
│ x = 5       │ (change here)
│ x = 10      │
└─────────────┘
        ↓
┌─────────────┐
│ Main Fn     │
│ x = 5 ✅    │ (unchanged!)
└─────────────┘

Pass by Reference (Arrays):
┌─────────────┐
│ Main Fn     │
│ arr[0]=97   │
└─────────────┘
        ↓ (gives address/reference)
┌─────────────┐
│ Function    │
│ arr[0]=97   │ (change here)
│ arr[0]=98   │
└─────────────┘
        ↓
┌─────────────┐
│ Main Fn     │
│ arr[0]=98 ✅│ (CHANGED!)
└─────────────┘
```

---

## 💻 Practical Example: Updating Array Elements

### 🔧 Problem:
Add 1 to all marks in an array through a function

### ✅ Solution:

```java
public class ArrayCC {
    
    // Function to update array (add 1 to each mark)
    public static void update(int marks[]) {
        // Loop through all indices
        for(int i = 0; i < marks.length; i++) {
            marks[i] = marks[i] + 1;
        }
    }
    
    // Function to print array elements
    public static void printMarks(int marks[]) {
        for(int i = 0; i < marks.length; i++) {
            System.out.print(marks[i] + " ");
        }
        System.out.println();
    }
    
    public static void main(String[] args) {
        // Create array with initial marks
        int marks[] = {97, 98, 99};
        
        // Print original marks
        System.out.println("Before update:");
        printMarks(marks);  // Output: 97 98 99
        
        // Call update function
        update(marks);
        
        // Print updated marks
        System.out.println("After update:");
        printMarks(marks);   // Output: 98 99 100
    }
}
```

---

## 🎯 Understanding the Function Syntax

### 📝 Declaring Array Parameter:

```java
public static void update(int marks[]) {
    // 'marks' is an array parameter
    // Same as: int marks[]
}
```

**Similar to regular variables:**
```
Regular variable:  public static void func(int x)
Array variable:    public static void func(int x[])
                                              ↑ Square brackets indicate array
```

---

## 🔁 The For Loop with Arrays

### ⚡ Most Important Loop Pattern:

```java
for(int i = 0; i < marks.length; i++) {
    // Do something with marks[i]
}
```

### 🔍 Breaking It Down:

| Part | Meaning |
|---|---|
| `int i = 0` | Start from index 0 |
| `i < marks.length` | Continue while index is within array bounds |
| `i++` | Move to next index |
| `marks[i]` | Access element at index i |

### 📊 Loop Flow Example (3-element array):

```
Iteration 1: i=0 → marks[0] → 97
Iteration 2: i=1 → marks[1] → 98
Iteration 3: i=2 → marks[2] → 99
Loop ends: i=3, not < 3
```

---

## 💻 Complete Step-by-Step Example

### 🏗️ Step 1: Create Array
```java
int marks[] = {97, 98, 99};
```

### 📤 Step 2: Print Original (Before)
```java
System.out.println("Before update:");
printMarks(marks);
// Output: 97 98 99
```

### 🔄 Step 3: Call Update Function
```java
update(marks);  // Passes reference to original array
```

### 🔍 Step 4: What Happens Inside update()
```java
public static void update(int marks[]) {
    for(int i = 0; i < marks.length; i++) {
        marks[i] = marks[i] + 1;  // Add 1 to each
    }
}

// Iteration 1: marks[0] = 97 + 1 = 98
// Iteration 2: marks[1] = 98 + 1 = 99
// Iteration 3: marks[2] = 99 + 1 = 100
```

### 📤 Step 5: Print Updated (After)
```java
System.out.println("After update:");
printMarks(marks);
// Output: 98 99 100
```

### 🖨️ Complete Output:
```
Before update:
97 98 99 
After update:
98 99 100
```

---

## ⚠️ Important: Regular Variables Don't Change!

### 🚫 Regular Variables Passed by Value:

```java
public class ArrayCC {
    
    public static void update(int marks[], int nonChangeable) {
        marks[0] = marks[0] + 1;      // ✅ Will change in main
        nonChangeable = nonChangeable + 5;  // ❌ Won't change in main
    }
    
    public static void main(String[] args) {
        int marks[] = {97, 98, 99};
        int nonChangeable = 5;
        
        update(marks, nonChangeable);
        
        System.out.println("marks[0] = " + marks[0]);           // 98 ✅ CHANGED
        System.out.println("nonChangeable = " + nonChangeable); // 5 ❌ UNCHANGED
    }
}
```

### 📊 Output:
```
marks[0] = 98
nonChangeable = 5
```

**Why?**
- `marks[]` is **passed by reference** → changes reflect
- `nonChangeable` is **passed by value** → changes don't reflect

---

## 🎨 Helper Function: Print Array

### 💡 Why Create a Print Function?

Instead of writing the same loop repeatedly:
```java
// Without function - repetitive
System.out.print(marks[0] + " ");
System.out.print(marks[1] + " ");
System.out.print(marks[2] + " ");
System.out.println();
```

Use a dedicated function:
```java
public static void printMarks(int marks[]) {
    for(int i = 0; i < marks.length; i++) {
        System.out.print(marks[i] + " ");
    }
    System.out.println();
}

// Now just call:
printMarks(marks);
```

---

## 📋 Common Patterns with Arrays

### ✅ Pattern 1: Update All Elements
```java
public static void updateAll(int arr[]) {
    for(int i = 0; i < arr.length; i++) {
        arr[i] = arr[i] + 1;
    }
}
```

### ✅ Pattern 2: Print All Elements
```java
public static void printAll(int arr[]) {
    for(int i = 0; i < arr.length; i++) {
        System.out.print(arr[i] + " ");
    }
    System.out.println();
}
```

### ✅ Pattern 3: Calculate Sum
```java
public static int calculateSum(int arr[]) {
    int sum = 0;
    for(int i = 0; i < arr.length; i++) {
        sum = sum + arr[i];
    }
    return sum;
}
```

### ✅ Pattern 4: Find Maximum
```java
public static int findMax(int arr[]) {
    int max = arr[0];
    for(int i = 1; i < arr.length; i++) {
        if(arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}
```

---

## 🔑 Key Concepts from Lecture 04

✅ Arrays are **always passed by reference**  
✅ Changes in function **reflect in calling function**  
✅ Regular variables are passed by value (no reflection)  
✅ The for loop `for(int i=0; i<arr.length; i++)` is **essential**  
✅ Use `arr[i]` to access element at index i  
✅ Create helper functions to avoid code repetition  
✅ `arr.length` gives array size for loop boundary  

---

## 🎯 Summary Table

| Concept | Detail |
|---|---|
| 📤 **Array Parameter** | `int marks[]` in function signature |
| 🔗 **Pass Method** | Always by reference |
| ♻️ **Changes** | Reflect in main function |
| 🔁 **Loop Pattern** | `for(int i=0; i<arr.length; i++)` |
| 🖨️ **Print Helper** | Avoids repetitive code |
| 🔄 **Update Helper** | Modifies array elements |

---

**Ready to explore more array operations and algorithms! 🚀**