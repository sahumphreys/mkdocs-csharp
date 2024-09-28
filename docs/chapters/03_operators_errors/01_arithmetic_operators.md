---
title: Arithmetic Operators
---

# {{ title }}

!!! note "From the syllabus"
    AQA: Be familiar with and be able to use ... (3.1.1.3/4.1.1.3)
    
    - Addition, subtraction, multiplication, real/float division, integer division (including remainders), exponentiation, rounding, truncation

The table summarises the standard set of arithmetic operators:

| Operator | Description | Example |
| -------- | ----------- | ------- |
|     +    |  Adds two values | `int n = a + b;` |
|     -    |  Subtracts two values | `int n = a - b;` |
|     *    |  Multiplies two values | `int n = a * b;` |
|     /    |  Divides dividend by divisor | `int n = a / b;` |
|     %    |  Modulus, remainder after integer division | `int n = a % b;` |
|    ++    |  Increment by one | `int n = a++;` |
|    --    |  Decrement by one | `int n = a--;` |

The operators for addition, subtraction, and multiplication should present no problems as these work just the same as in Mathematics. However, division is less straightforward. When you divide an integer by another integer in C#, the result is also an integer, specifically the integer part of the answer, ignoring anything after the decimal point. The result is always truncated (rounded down), not rounded to the nearest integer.

For example:

```cs
int cake = 15;
cake = cake / 4; // cake will be 3
```

In this case, the variable `cake` will contain `3`, not `3.75`. Conversely, if you use a `double` type:

```cs
double cake = 15;
cake = cake / 4; // cake will be 3.75
```

Now, `cake` will correctly hold `3.75` as it can store decimal values.

The modulus operator `%` performs integer division but returns the remainder. For instance, `9 % 2` yields `1`.

!!! warning
    Integer division by `0` will result in a runtime error, so always ensure your divisor is not zero.

For incrementing and decrementing, C# offers convenient operators:

```cs
int age = 45;
age++; // age is now 46
int x = 3;
x--; // x is now 2
```

The `++` operator increments a variable, while `--` decrements it. These operators can be used either as postfix or prefix, yielding different results:

```cs
int a = 4;
int b = 5;
Console.WriteLine(a + (b++));   // Outputs 9
Console.WriteLine(a + b);       // Outputs 10 (b is now 6)
Console.WriteLine(a + (++b));   // Outputs 11 (b is incremented before the addition)
Console.WriteLine(a + b);       // Outputs 11
```

What will be printed to the screen after each operation? If you’re uncertain, write the code and check!

C# does not have an operator for exponentiation. Instead, we use the `Math` class:

```cs
double Result = Math.Pow(2, 3); // Result is 8
```

Both parameters must be `double`, and the result is also a `double`.

To round or truncate values, we utilize methods from the `Math` class. Here’s an illustration:

```cs
float Number = 3.456789f;
Console.WriteLine(Number);                  // Outputs 3.456789
Console.WriteLine(Math.Round(Number, 2));   // Outputs 3.46
Console.WriteLine(Math.Truncate(Number));    // Outputs 3
```
