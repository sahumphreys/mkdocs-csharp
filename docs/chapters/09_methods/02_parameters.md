---
title: Parameters
---

# {{ title }}

Often, methods need additional information to perform their tasks. This information is passed to methods through **parameters**.

Let's start with a simple example. Suppose we need a method that returns the square of the number 5:

```csharp
static int SquareOfFive()
{
    return 5 * 5;
}
```

This method will always return 25, the square of 5. But what if we want a method that can return the square of _any_ number, not just 5? For this, we need to pass a value to the method for it to work on.

## Generalizing with Parameters

Here's a generalized version of the method:

```csharp
static int SquareNum(int number)
{
    return number * number;
}
```

Now, our method can calculate the square of any integer we provide as a parameter:

```csharp
int x = SquareNum(5);  // x will be 25
int y = 53;
int z = SquareNum(y);  // z will be 2809
```

In the example above, the `SquareNum` method takes an **integer parameter** `number`. When we call the method, we pass an **argument** (like `5` or `y`) that gets copied into the `number` parameter within the method. The method then performs its calculation using this value.

### Key Concepts:

- **Parameter**: A variable used in a method definition that receives a value when the method is called.
- **Argument**: The actual value passed to the method when it is invoked. For example, in `SquareNum(5)`, the number `5` is the argument, and `number` is the parameter in the method definition `SquareNum(int number)`.

### Best Practices for Parameters

When designing methods, it's essential to look for opportunities to **generalize** the method. This means making the method flexible enough to handle a range of inputs, not just specific values. This can make your code more reusable and efficient.

**Example:**

```csharp
int num = 7;
int numSquared = SquareNum(num); // numSquared will be 49
```

Here, we pass the variable `num` as an argument to the `SquareNum` method. The method then calculates the square of `num` and returns the result.

## Multiple Parameters

A method can take multiple parameters, separated by commas. However, be cautious not to overload the method with too many parameters, as it can make the method difficult to use and understand. If a method has too many parameters, consider splitting it into smaller, more manageable methods.

**Example of multiple parameters:**

```csharp
static void PrintSumAndProduct(int a, int b)
{
    Console.WriteLine($"Sum: {a + b}");
    Console.WriteLine($"Product: {a * b}");
}

PrintSumAndProduct(3, 4);  // Output: Sum: 7, Product: 12
```

### Important Rules for Parameters

1. **Each parameter must have a type declared**: You cannot omit the data type, even if multiple parameters are of the same type.

   ```csharp
   // Incorrect
   static void MyMethod(int x, y, z) { }
   
   // Correct
   static void MyMethod(int x, int y, int z) { }
   ```

2. **Order matters**: When calling a method with multiple parameters, the order of arguments must match the order of parameters in the method definition.

   ```csharp
   static void PrintCoordinates(int x, int y)
   {
       Console.WriteLine($"X: {x}, Y: {y}");
   }

   PrintCoordinates(10, 20);  // Correct
   // PrintCoordinates(20, 10);  // Incorrect, unless this is intended
   ```

3. **No parameters**: If a method does not take any parameters, the parentheses `()` cannot be omitted.

   ```csharp
   static void PrintHello()
   {
       Console.WriteLine("Hello!");
   }

   PrintHello();  // Correct
   ```

## Default Parameters

In C#, you can provide a **default value** for a parameter. This means that if the caller does not provide an argument for that parameter, the method will use the default value instead.

**Example:**

```csharp
static int SquareNum(int n = 5)
{
    return n * n;
}

int result1 = SquareNum();  // result1 will be 25, as the default value of n is used
int result2 = SquareNum(3); // result2 will be 9, as 3 is passed as an argument
```

Here, the `SquareNum` method has a default parameter value of `5`. If we call `SquareNum()` without providing an argument, it uses the default value `5`. If we provide an argument, like `3`, it uses that value instead.

### Summary

Understanding how to work with parameters is crucial for writing flexible and reusable methods. Always strive to design methods that can handle a variety of inputs, and be mindful of the rules and best practices around parameters and arguments. By doing so, you'll be able to create more robust and maintainable code.
