# 📚 Module: Arrays (Part - I) | Lecture 03: Arrays - Input, Output and Update

---

## 🎯 Three Main Operations

| Operation | Purpose | Method |
|---|---|---|
| ➡️ **Input** | Store values in array | `sc.nextInt()` |
| ⬅️ **Output** | Display values from array | `System.out.println()` |
| ♻️ **Update** | Modify existing values | Direct assignment |

---

## 📥 Taking Input from Array

### 🔧 Setup: Scanner Object

Before taking input, we need a **Scanner object**:

```java
import java.util.Scanner;

public class ArrayCC {
    public static void main(String[] args) {
        // Create Scanner object
        Scanner sc = new Scanner(System.in);
        
        // Create array of size 100
        int marks[] = new int[100];
    }
}
```

⚠️ **Important:** Don't forget the `import` statement at the top!

---

### 📝 Taking Input for Each Element

To input values into specific array indices:

```java
// Input for Physics marks (index 0)
marks[0] = sc.nextInt();

// Input for Chemistry marks (index 1)
marks[1] = sc.nextInt();

// Input for Maths marks (index 2)
marks[2] = sc.nextInt();
```

**How it works:**
- `marks[index]` = specific location in array (like a variable)
- `sc.nextInt()` = takes integer input from user
- Value is stored at that index

---

## 📤 Output: Printing Array Elements

### 🖨️ Print Individual Elements

```java
System.out.println(marks[0]);  // Physics marks
System.out.println(marks[1]);  // Chemistry marks
System.out.println(marks[2]);  // Maths marks
```

**Key Concept:**
- Each `marks[index]` acts as a **single variable**
- Treat it like any other variable for printing

---

### 💻 Complete Example: Input & Output

```java
import java.util.Scanner;

public class ArrayCC {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int marks[] = new int[100];
        
        // INPUT: Take 3 marks
        marks[0] = sc.nextInt();  // Physics
        marks[1] = sc.nextInt();  // Chemistry
        marks[2] = sc.nextInt();  // Maths
        
        // OUTPUT: Print the marks
        System.out.println(marks[0]);
        System.out.println(marks[1]);
        System.out.println(marks[2]);
    }
}
```

### 📊 Sample Execution:

```
User Input:
97
99
95

Output:
97
99
95
```

---

## ♻️ Update: Modifying Array Values

### 🔄 Simple Update

```java
// Original value at index 2 is 95
marks[2] = 98;  // Update to 98
```

**Use Case:** Correcting a mistake or changing a value

---

### 🧮 Update with Mathematical Operations

#### ➕ Adding to Existing Value:
```java
marks[2] = marks[2] + 1;
// If original was 95, now becomes 96
```

#### 🔢 Other Operations:
```java
marks[2] = marks[2] - 5;   // Subtract
marks[2] = marks[2] * 2;   // Multiply
marks[2] = marks[2] / 10;  // Divide
```

---

### 💡 Complete Update Example

```java
import java.util.Scanner;

public class ArrayCC {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int marks[] = new int[100];
        
        // INPUT
        marks[0] = sc.nextInt();
        marks[1] = sc.nextInt();
        marks[2] = sc.nextInt();
        
        // OUTPUT - Original values
        System.out.println("Original marks:");
        System.out.println(marks[0]);
        System.out.println(marks[1]);
        System.out.println(marks[2]);
        
        // UPDATE - Add 1 to Maths marks
        marks[2] = marks[2] + 1;
        
        // OUTPUT - Updated values
        System.out.println("Updated marks:");
        System.out.println(marks[0]);
        System.out.println(marks[1]);
        System.out.println(marks[2]);
    }
}
```

### 📊 Sample Execution:

```
Input: 98, 99, 95

Original marks:
98
99
95

Updated marks (after adding 1 to Maths):
98
99
96
```

---

## 🎓 Calculations with Array Elements

### 📐 Calculating Average/Percentage

```java
// Calculate average of 3 marks
int percentage = (marks[0] + marks[1] + marks[2]) / 3;

System.out.println("Percentage = " + percentage + "%");
```

### 💻 Complete Example with Calculation:

```java
import java.util.Scanner;

public class ArrayCC {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int marks[] = new int[100];
        
        // INPUT
        marks[0] = sc.nextInt();  // Physics
        marks[1] = sc.nextInt();  // Chemistry
        marks[2] = sc.nextInt();  // Maths
        
        // CALCULATION
        int percentage = (marks[0] + marks[1] + marks[2]) / 3;
        
        // OUTPUT
        System.out.println("Percentage = " + percentage + "%");
    }
}
```

### 📊 Sample Execution:

```
Input: 98, 99, 95

Output:
Percentage = 97%
```

---

## 📏 Array Length Property

### 🔍 What is `.length`?

Every array in Java has a special property called **`.length`** that gives the **total size** of the array.

### 📝 Syntax:
```java
arrayName.length
```

---

### 💻 Example: Using `.length`

```java
int marks[] = new int[100];

System.out.println("Length of array = " + marks.length);
```

**Output:**
```
Length of array = 100
```

---

### ⚠️ Important Points About `.length`:

| Aspect | Detail |
|---|---|
| 📊 **Size** | Returns the **total capacity** of array |
| 🔗 **Operator** | Uses **dot operator (.)** |
| 📝 **Syntax** | `arrayName.length` (no parentheses) |
| 🔄 **Dynamic** | Reflects actual array size, not elements used |

---

### 📌 Key Difference:

```java
int marks[] = new int[100];

marks[0] = 95;
marks[1] = 98;
marks[2] = 92;

System.out.println(marks.length);  // Output: 100
// NOT 3! Because array capacity is 100, even though we used only 3 indices
```

---

## 🎨 Visual Summary: Input → Output → Update

```
┌──────────────────────────────────────────┐
│ Array Creation                           │
│ int marks[] = new int[100];              │
└──────────────────────────────────────────┘
                    ↓
┌──────────────────────────────────────────┐
│ INPUT (Fill with values)                 │
│ marks[0] = sc.nextInt();                 │
│ marks[1] = sc.nextInt();                 │
│ marks[2] = sc.nextInt();                 │
└──────────────────────────────────────────┘
                    ↓
┌──────────────────────────────────────────┐
│ OUTPUT (Display values)                  │
│ System.out.println(marks[0]);            │
│ System.out.println(marks[1]);            │
│ System.out.println(marks[2]);            │
└──────────────────────────────────────────┘
                    ↓
┌──────────────────────────────────────────┐
│ UPDATE (Modify values)                   │
│ marks[2] = marks[2] + 1;                 │
└──────────────────────────────────────────┘
                    ↓
┌──────────────────────────────────────────┐
│ OUTPUT AGAIN (Display updated values)    │
│ System.out.println(marks[2]);            │
└──────────────────────────────────────────┘
```

---

## 🔑 Key Concepts from Lecture 03

✅ Use `Scanner` object for taking input  
✅ Each `array[index]` can be treated as a single variable  
✅ Input using `sc.nextInt()` method  
✅ Output using `System.out.println()`  
✅ Update values with direct assignment or mathematical operations  
✅ Calculate averages, percentages, or any formula using array elements  
✅ Use `array.length` to get total array size  
✅ Array size is **fixed** - `length` returns capacity, not elements used  

---

**Ready for more advanced array operations! 🚀**