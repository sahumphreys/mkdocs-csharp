---
title: Overloading Methods
---

In C#, it is possible to have multiple methods with the same name in the same class, as long as they differ in their parameters. This concept is known as **method overloading**.

## What is Method Overloading?

Method overloading allows you to define multiple methods with the same name but different **parameter lists**. The methods must be distinguishable by:
- The **number of parameters**, or
- The **data types of the parameters**.

This enables the use of a single method name for similar actions, improving readability and reducing the need for overly descriptive method names.

## Example: Overloading by Data Type

```csharp
static int AddThree(int a, int b, int c)
{
    return a + b + c;
}

static double AddThree(double a, double b, double c)
{
    return a + b + c;
}
```

Here, two `AddThree()` methods are defined:
- The first takes three `int` parameters.
- The second takes three `double` parameters.

When you call `AddThree()` with three integers, the first method is executed. When you call it with three doubles, the second method is executed.

**Advantages:**
- Simplifies method names: Instead of `AddThreeIntegers()` and `AddThreeDoubles()`, you use just `AddThree()`.
- Enhances code clarity by grouping similar operations under a single method name.

## Example: Overloading by Number of Parameters

```csharp
static int Add(int a, int b)
{
    return a + b;
}

static int Add(int a, int b, int c)
{
    return a + b + c;
}
```

In this example, both methods are named `Add()`, but the first one takes two parameters, while the second takes three. The correct method is chosen based on the number of arguments passed.

## Important Note

It is **not** permissible to overload methods by changing only the **return type**. For example:

```csharp
// This is NOT allowed
static int Add(int a, int b) { return a + b; }
static double Add(int a, int b) { return a + b; }
```

The above code will result in a compilation error because the methods have the same name, parameters, and the compiler cannot distinguish between them based on the return type alone.

## Example: Bubble Sort Revisited

Let's revisit the bubble sort algorithm we discussed earlier. Here is the original code:

```csharp
using System;

namespace BubbleSort
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] myArray = { 23, 16, 9, 86, 54, 3 };
            int temp;

            Console.Clear();
            Console.WriteLine("Initial contents of the array:");
            foreach (int i in myArray)
            {
                Console.Write($"{i} ");
            }

            int current = myArray.Length - 1;

            for (int i = 0; i < myArray.Length - 1; i++)
            {
                for (int j = 0; j < myArray.Length - 1; j++)
                {
                    if (myArray[j] > myArray[j + 1])
                    {
                        temp = myArray[j];
                        myArray[j] = myArray[j + 1];
                        myArray[j + 1] = temp;
                    }
                }
            }

            Console.WriteLine("\nSorted array:");
            foreach (int i in myArray)
            {
                Console.Write($"{i} ");
            }
        }
    }
}
```

### Identifying Repeated Code

1. **Printing the Array**: The array is printed twice, once before and once after sorting. This is a good candidate for a separate method.
2. **Swapping Elements**: The swap operation is performed within the sorting loop. Extracting this into a separate method makes the sorting logic clearer.

### Refactoring Using Methods

#### Step 1: Create a Method for Printing the Array

```csharp
static void PrintArray(int[] array)
{
    foreach (int i in array)
    {
        Console.Write($"{i} ");
    }
    Console.WriteLine();
}
```

Call this method instead of repeating the print logic:

```csharp
Console.WriteLine("Initial contents of the array:");
PrintArray(myArray);

// ... sorting logic ...

Console.WriteLine("Sorted array:");
PrintArray(myArray);
```

#### Step 2: Create a Method for Swapping Elements

```csharp
static void Swap(ref int a, ref int b)
{
    int temp = a;
    a = b;
    b = temp;
}
```

Use this method in the sorting logic:

```csharp
for (int i = 0; i < myArray.Length - 1; i++)
{
    for (int j = 0; j < myArray.Length - 1; j++)
    {
        if (myArray[j] > myArray[j + 1])
        {
            Swap(ref myArray[j], ref myArray[j + 1]);
        }
    }
}
```

### Step 3: Decompose into More Methods

You can further decompose the code into separate methods like `InitializeArray()` and `SortArray()` for better organization.

#### Final Version

```csharp
using System;

namespace BubbleSort
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] myArray = InitializeArray();
            Console.WriteLine("Initial contents of the array:");
            PrintArray(myArray);

            SortArray(myArray);

            Console.WriteLine("Sorted array:");
            PrintArray(myArray);
        }

        static int[] InitializeArray()
        {
            return new int[] { 23, 16, 9, 86, 54, 3 };
        }

        static void PrintArray(int[] array)
        {
            foreach (int i in array)
            {
                Console.Write($"{i} ");
            }
            Console.WriteLine();
        }

        static void Swap(ref int a, ref int b)
        {
            int temp = a;
            a = b;
            b = temp;
        }

        static void SortArray(int[] array)
        {
            for (int i = 0; i < array.Length - 1; i++)
            {
                for (int j = 0; j < array.Length - 1; j++)
                {
                    if (array[j] > array[j + 1])
                    {
                        Swap(ref array[j], ref array[j + 1]);
                    }
                }
            }
        }
    }
}
```

### Advantages of Decomposition

- **Code Reusability**: Methods like `PrintArray()` and `Swap()` can be reused in other sorting algorithms.
- **Simpler Maintenance**: If a bug is found in the swap logic, it can be fixed in one place.
- **Improved Readability**: Breaking down the code into smaller methods makes it easier to understand.

### Key Takeaways

- Method overloading enhances readability and reduces the need for verbose method names.
- Decomposing complex problems into smaller methods improves code structure and maintainability.
- Avoid code duplication by creating reusable methods for repeated tasks.
