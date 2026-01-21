# 📚 Module: Arrays (Part - I) | Lecture 02: Arrays Creation

---

## 🔧 Basic Operations on Arrays

Every data structure has fundamental operations. For arrays, we'll cover:

| Operation | Description |
|---|---|
| 🔨 **Create** | How to create an array |
| ➡️ **Input** | How to insert elements into array |
| ⬅️ **Output** | How to retrieve elements from array |
| ♻️ **Update** | How to modify values at specific indices |

---

## 🏗️ Array Creation Syntax

### 📝 General Syntax:
```
DataType arrayName[] = new DataType[size];
```

### 🔍 Breaking Down the Syntax:

| Component | Purpose | Example |
|---|---|---|
| **DataType** | Type of elements to store | `int`, `String`, `float`, `char`, `double` |
| **arrayName** | Name of the array (user-defined) | `marks`, `numbers`, `fruits` |
| **[ ]** | Square brackets (must have) | Indicates it's an array |
| **new** | Keyword to allocate memory | Finds free space in memory |
| **[size]** | Number of elements to store | `50`, `100`, `5` |

---

## 💻 Code Examples

### ✅ Example 1: Integer Array (50 elements)
```java
public class ArrayCC {
    public static void main(String[] args) {
        int marks[] = new int[50];
    }
}
```

**What happens:**
- ✔️ **Declaration:** `int marks[]` - tells Java we need an array
- ✔️ **Creation:** `new int[50]` - actually creates the array in memory
- ✔️ **Size:** 50 integer values can be stored

---

### ✅ Example 2: Array with Direct Values (Auto-size)
```java
int numbers[] = {1, 2, 3};
```

**What happens:**
- Java **automatically detects** the size = 3
- No need to specify `new` keyword
- Array is created with exactly 3 elements

---

### ✅ Example 3: Another Integer Array
```java
int moreNumbers[] = {4, 5, 6};
```

---

### ✅ Example 4: String Array
```java
String fruits[] = {"Apple", "Mango", "Banana"};
```

**Details:**
- Type: `String`
- Size: 3 (auto-detected)
- Stores three fruit names

---

## ⚡ Important Characteristic: Static Size

### 🚫 Arrays Are Fixed Size!

Once created, **you cannot change the array size** during runtime:

```java
int marks[] = new int[50];

// ✅ Can store 50 marks
marks[0] = 95;
marks[49] = 88;

// ❌ CANNOT store 51st mark
marks[50] = 92;  // ERROR - Index out of bounds!
```

### 📌 Key Point:
```
If you need to change size → you must change it in code BEFORE execution
You CANNOT change it during program execution (runtime)
```

---

## 🎯 Default Values in Arrays

### 📍 When You Don't Initialize Elements:

When an array is created but elements aren't explicitly set, they get **default values**:

| Data Type | Default Value |
|---|---|
| `int` | `0` |
| `float` | `0.0` |
| `double` | `0.0` |
| `String` | `null` (empty string) |
| `char` | `\0` (empty character) |
| `boolean` | `false` |

### 📊 Example:
```java
int marks[] = new int[50];
// All 50 positions contain 0 by default
// marks[0] = 0
// marks[1] = 0
// marks[2] = 0
// ... up to marks[49] = 0
```

---

## 📋 Alternative Syntax (Declaration Only)

Without using `new` keyword - auto-detect size:
```java
int marks[] = {85, 90, 88};
// Size automatically = 3
```

vs.

With `new` keyword - specify size:
```java
int marks[] = new int[50];
// Size explicitly = 50
// All initialized to 0 by default
```

---

## 🎨 Visual Summary

### Creation Process:

```
Step 1: Declare
┌─────────────────────┐
│ int marks[]         │
└─────────────────────┘

Step 2: Allocate Memory with 'new'
┌─────────────────────┐
│ new int[50]         │
└─────────────────────┘
     ↓ Creates 50 slots in memory

Step 3: Complete Statement
┌──────────────────────────────────┐
│ int marks[] = new int[50];       │
└──────────────────────────────────┘
```

---

## 🔑 Key Takeaways (Lecture 02)

✅ Arrays are created using `new` keyword  
✅ Size is **fixed and cannot change** during execution  
✅ Default values: `0` for numbers, `null` for strings  
✅ Can initialize with values: `{1, 2, 3}` or manually specify size  
✅ Declaration vs Creation are **two different steps**

---

**Ready for the next operations: Input, Output, and Update! 🚀**