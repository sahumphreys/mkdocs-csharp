---
title: Declaring and Allocating Memory for Arrays
---

# {{ title }}

In C#, arrays have a fixed length that is set when they are declared and **cannot** be changed later. This means arrays in C# are **static**.

### Declaring an Array

To declare an array, use the following syntax:

```cs
int[] myArray;
```

- The `int` keyword specifies the data type of the array elements.
- The square brackets `[]` indicate that `myArray` is an array of integers, not a single integer.
- This line **only** creates a **reference** to the array on the stack. The array itself has not been created yet, and the memory required to hold the data has not been allocated. Attempting to use `myArray` at this point would result in a `NullReferenceException` because no memory has been allocated for the array elements.

!!! note
    A **reference** in this context is a variable that is pointing to an array object, that is an address for the start of the array object.

### Allocating Memory for an Array

To allocate memory for the array, use the `new` keyword:

```cs
myArray = new int[6];
```

- This statement creates six consecutive memory locations on the heap, each capable of holding an integer value.
- All elements are initialized with the default integer value of `0`.

!!! note
  Any numeric data type will be initialised to $0$; the `bool` data type defaults to `false`.

Let’s visualize what happens in memory:

<figure markdown="1">
  ![Uninitialized memory](../../assets/images/ArrayStack1.png){ width="500" }
  <figcaption>Uninitialized Memory: `myArray` points to `null`.</figcaption>
</figure>

<figure markdown="1">
  ![Initialized memory](../../assets/images/ArrayStack2.png){ width="600" }
  <figcaption>Initialized Memory: `myArray` now points to the start address of a block of memory containing six integers, all initialized to `0`.</figcaption>
</figure>

### Initializing an Array with Values

You can also initialize the array with specific values when declaring it:

```cs
int[] myArray = { 23, 16, 9, 86, 54, 3 };
```

In this case:
- The length of the array is inferred from the number of elements provided.
- The array `myArray` is created with six elements, initialized to the values specified in the curly braces.

Similarly, you can create and initialize an array of strings:

```cs
string[] primates = { "Gorilla", "Ape", "Lemur", "Simian" };
```

!!! note
    The curly braces `{}` are used to initialize the array with values directly.

### Common Mistakes to Avoid
1. **Accessing Elements Before Initialization:**
   Attempting to use an array before allocating memory with the `new` keyword will result in a `NullReferenceException`.
   
2. **Changing Array Length:**
   Once created, the length of an array cannot be changed. If you need a resizable collection, consider using a `List<T>` instead.
