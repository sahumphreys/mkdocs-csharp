---
title: Passing by Value, Passing by Reference
---

You've likely encountered the terms **value** and **reference** before. These terms are significant when discussing parameters in methods as well. Let's explore the differences with some examples.

## Passing by Value

Consider the following code and try to predict what will be displayed on the screen:

```csharp
class Program
{
    static void Main(string[] args)
    {
        int value = 3;
        Console.WriteLine($"In Main(), value is equal to {value}");
        AddFive(value);
        Console.WriteLine($"Back in Main(), value is equal to {value}");
    }

    static void AddFive(int x)
    {
        x = x + 5;
        Console.WriteLine($"In AddFive(), value is now {x}");
    }
}
```

**Expected Output:**

```bash
In Main(), value is equal to 3
In AddFive(), value is now 8
Back in Main(), value is equal to 3
```

Did you predict correctly?

When the variable `value` is passed to the method `AddFive()`, only the **value** of `value` is copied to the parameter `x`. This means a new memory location is created for `x`, and the value `3` is stored there. Changes to `x` inside the `AddFive()` method do not affect the original `value` variable in `Main()`. This is known as **passing by value**.

### Key Concepts:

- **Passing by Value**: A copy of the variable's value is passed to the method. Any changes made to the parameter inside the method do not affect the original variable.
- **Memory Allocation**: A new block of memory is allocated for the parameter when a method is called. When the method ends, this memory is released.

## Passing by Reference

Now, consider this code:

```csharp
class Program
{
    static void Main(string[] args)
    {
        int[] myArray = { 2, 3, 4 };
        for (int i = 0; i < myArray.Length; i++)
        {
            Console.Write($"{myArray[i]} ");
        }
        Console.WriteLine();

        AddTen(myArray);

        for (int i = 0; i < myArray.Length; i++)
        {
            Console.Write($"{myArray[i]} ");
        }
    }

    static void AddTen(int[] x)
    {
        for (int i = 0; i < x.Length; i++)
        {
            x[i] += 10;
        }
    }
}
```

**Expected Output:**

```bash
2 3 4 
12 13 14 
```

An array is a **reference type**. When `myArray` is passed to the `AddTen()` method, it passes a reference (memory address) to the array, not a copy of its values. Therefore, changes made to `x` inside `AddTen()` affect the original array `myArray` in `Main()`. This is called **passing by reference**.

### Key Concepts:

- **Passing by Reference**: A reference (memory address) to the original variable is passed to the method. Changes made to the parameter inside the method affect the original variable.
- **Reference Types**: Arrays, objects, and other complex types in C# are reference types. When passed as arguments, the method can modify the original data.

### Passing Value Types by Reference

It is also possible to pass a value type (like `int`) by reference using the `ref` keyword. This allows the method to modify the original value.

**Example:**

```csharp
class Program
{
    static void Main(string[] args)
    {
        int value = 3;
        Console.WriteLine($"In Main(), value is initially {value}");
        AddFive(ref value);
        Console.WriteLine($"Back in Main(), value is now {value}");
    }

    static void AddFive(ref int x)
    {
        x = x + 5;
        Console.WriteLine($"In AddFive(), value is now {x}");
    }
}
```

**Expected Output:**

```bash
In Main(), value is initially 3
In AddFive(), value is now 8
Back in Main(), value is now 8
```

Using `ref` allows the method to modify the original `value` variable. Both the method definition and the method call must include the `ref` keyword.

## Summary

- **Passing by Value**: Copies the value to the method. Changes do not affect the original variable.
- **Passing by Reference**: Passes a reference to the method. Changes affect the original variable.
- **`ref` Keyword**: Allows value types to be passed by reference, enabling the method to modify the original variable.

## Local and Global Variables

You may remember from earlier chapters the difference between **local** and **global** variables. These terms describe the **scope** of a variable.

### Local Variables

A **local variable** is declared and used within a specific block of code, such as a method, loop, or conditional statement. It is only accessible within that block.

**Example:**

```csharp
static void Main(string[] args)
{
    int total;
    IncreaseTotal();
    Console.WriteLine(total);  // This will cause a compilation error
}

static void IncreaseTotal()
{
    int total = 10;
}
```

In this example, the `total` variable in `Main()` and the `total` variable in `IncreaseTotal()` are different variables, each with its own memory. Modifying one does not affect the other.

**Common Mistake:**

```csharp
static void MyMethod()
{
    for (int i = 0; i < 10; i++)
    {
        Console.WriteLine(i);
    }
    Console.WriteLine(i);  // Error: 'i' does not exist outside the loop
}
```

Here, the variable `i` is local to the `for` loop and cannot be accessed outside of it. This will result in a compilation error.

### Global Variables

A **global variable** is accessible from anywhere in the program. In C#, global variables are typically declared as `static` fields of a class. They are rarely used due to potential issues such as unintended side effects and difficulty in debugging.

**Example:**

```csharp
class Program
{
    static int total = 0;

    static void Main(string[] args)
    {
        IncreaseTotal();
        Console.WriteLine(total);  // This will print 10
    }

    static void IncreaseTotal()
    {
        total += 10;
    }
}
```

In this example, the variable `total` is accessible from both `Main()` and `IncreaseTotal()` because it is a static field of the `Program` class.

### Advantages of Local Variables

- **Isolation**: Local variables are confined to their scope, preventing unexpected changes from other parts of the program.
- **Memory Management**: Local variables are destroyed once the block of code they belong to is finished, freeing up memory.
- **Reusability**: Functions and methods using local variables are easier to test and reuse in different contexts without side effects.

### Best Practices

- Use **local variables** whenever possible to limit the scope of data and reduce the risk of accidental changes.
- Avoid using **global variables** unless absolutely necessary, and prefer passing data explicitly through method parameters.
