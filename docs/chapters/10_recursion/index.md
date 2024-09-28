---
title: Recursion
---

!!! note "In this chapter"
    - Understand the principle of __recursion__.
    - Compare __recursion__ to __iteration__.
    - Review the role played by the __stack__ in recursive solutions.
    - Recognize potential recursive solutions to problems.
    - Understand the need for a __base case__ to exit from a recursive method.

## Introduction

Recursion can be a challenging topic for many students, and it is often introduced later in programming or computer science courses. Although defining and explaining recursion is straightforward, identifying when and how to use it effectively can be more complex. In this section, we will explore the basics of recursion and how it compares to iteration, laying the groundwork for deeper discussions later on.

## Iteration vs. Recursion

When we encounter a problem that requires repeating a set of instructions, we typically use loops to iterate over those instructions. This is known as __iteration__. For instance, if we want to print the integers between two given values, `a` and `b`, we can use a `for` loop:

```csharp
static void PrintValues(int a, int b)
{
    for (int i = a; i < b; i++)
    {
        Console.Write($"{i}, ");
    }
    Console.WriteLine(b);
}
```

This code iterates from `a` to `b`, printing each value. However, we can also solve this problem using __recursion__.

## What is Recursion?

Recursion occurs when a function calls itself to solve a smaller instance of the same problem. A recursive function typically consists of two parts:

1. **Base Case**: The condition that stops the recursion, preventing an infinite loop.
2. **Recursive Case**: The part of the function where the function calls itself with modified arguments, moving the problem closer to the base case.

Let's rewrite the above example using recursion:

```csharp
static void PrintValues(int a, int b)
{
    if (a == b)
    {
        Console.Write(b);
    }
    else
    {
        Console.Write($"{a}, ");
        PrintValues(a + 1, b);
    }
}
```

In this recursive version:

- **Base Case**: When `a` is equal to `b`, the function simply prints `b` and stops. This ensures that the function does not call itself indefinitely.
- **Recursive Case**: The function prints the current value of `a` and then calls itself with `a + 1` as the new argument. This moves the problem closer to the base case.

## Comparing Recursion and Iteration

### Similarities:
- Both recursion and iteration are used to repeat a set of instructions.
- Any problem that can be solved with iteration can also be solved with recursion and vice versa.

### Differences:
- **Iteration** uses loop constructs (`for`, `while`, etc.) and relies on a counter or condition to stop.
- **Recursion** uses function calls and depends on a base case to terminate.

### When to Use Recursion:

Recursion is often more intuitive for problems that have a natural "self-similar" structure, such as:

- **Factorial Calculation**: `n! = n * (n - 1)!`
- **Fibonacci Sequence**: `F(n) = F(n - 1) + F(n - 2)`
- **Tree Traversal**: Exploring nodes in a tree-like structure.

However, recursion can be less efficient in terms of memory and execution time because each recursive call adds a new entry to the call stack.

## The Role of the Stack in Recursion

When a recursive function calls itself, the state of the current function (variables, return address, etc.) is pushed onto the __call stack__. Each recursive call creates a new stack frame, which holds the function's parameters and local variables.

If the base case is not reached, the stack will keep growing, leading to a __stack overflow__. This occurs when the call stack exceeds its limit, usually due to deep or infinite recursion.

## Summary

Recursion is a powerful tool in programming that allows for elegant and concise solutions to certain types of problems. Understanding its relationship with the call stack and the importance of a base case is crucial. As we continue to explore recursion in more depth, we will look at more complex examples and best practices for using recursion effectively.