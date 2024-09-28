---
title: Recursion Explained
---

# {{ title }}

!!! note "From the syllabus"
    AQA: Recursive Techniques (3.1.1.10/4.1.1.16): 
    - Be familiar with the use of recursive techniques in programming languages (general and base cases and the mechanism for implementation).
    - Be able to solve simple problems using recursion.

**Recursion** is a method of solving a problem where the solution depends on solutions to smaller instances of the same problem. Most programming languages support recursion by allowing a function to call itself from within its own code.

Here's a tongue-in-cheek dictionary definition of __recursion__:

- __Recursion__: see Recursion

## What is Recursion?

Recursion is a technique where a method calls itself with a smaller or simpler version of the original problem. This can be a powerful way to solve problems that have a repetitive or nested structure.

To understand how this works, let’s revisit the example from the previous section with `a = 1` and `b = 5`. 

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


When `PrintValues(1, 5)` is called, the first statement in the `else` clause will print `1` to the screen. The method then calls itself with the updated values `a = 2` and `b = 5`. 

It's crucial to note that the first method call has not yet finished its execution when it calls itself again. We will explore this in more detail later. After several more recursive calls, the values will eventually be `a = 5` and `b = 5`. This is the terminating condition or __base case__. At this point, the `if` clause will be executed, and the method will stop calling itself. This termination prevents infinite recursion.

Once the base case is reached, the method will start to __unwind__. This means that each previous call will complete in reverse order, one by one, until the initial call finishes and control is returned to the calling program.

## The Importance of a Base Case

The base case is essential for recursion to work correctly. Without a base case, the function will continue to call itself indefinitely, leading to an infinite recursion. This will eventually cause a stack overflow, crashing the program because the call stack—the memory area where function calls are stored—will run out of space.

## Why Use Recursion?

This example may seem straightforward, but the real challenge is recognizing when, where, and how to use recursion effectively. When used correctly, recursion can provide elegant solutions to complex problems. It can simplify your code and reduce the complexity of your logic.

The trick is to:

1. **Identify a simpler version of the problem** that you can solve more easily.
2. **Express the original problem in terms of this simpler case**.
3. **Apply recursion** until the problem reduces to its simplest form (the base case), and then all the other steps will automatically resolve themselves.

This may seem magical, but it’s a logical consequence of breaking down a problem into smaller and smaller pieces until it becomes trivial to solve.

## A Visual Analogy

To visualize recursion, think of a set of nested Russian dolls. Each smaller doll fits inside a larger one, just like how each recursive call fits inside the previous one. The process continues until we reach the smallest doll, representing the base case. Afterward, the dolls are closed back in reverse order, similar to how recursive calls return and complete.

<figure markdown="span">
  ![Russian Dolls](../../assets/images/dolls.jpg){ width="300" }
  <figcaption>Recursion - with Russian Dolls</figcaption>
</figure>

## Why is Recursion Important?

Recursion is one of the most fundamental ideas in computer science. Although it can be challenging to grasp at first, mastering recursion opens up new ways of thinking about problem-solving. It is particularly useful for problems that involve:

- **Tree structures** (e.g., parsing expressions, navigating file systems).
- **Divide-and-conquer algorithms** (e.g., quicksort, mergesort).
- **Mathematical problems** (e.g., calculating factorials, generating Fibonacci sequences).

Finding recursive solutions requires a combination of logical thinking, practice, and sometimes even intuition. But with experience, it becomes an invaluable tool for solving complex problems.

## Key Points to Remember

- Each call to a recursive function should bring the problem closer to the base case.
- Ensure that your recursive function has a clearly defined base case to prevent infinite recursion.
- Recursion is not always the best solution; consider whether an iterative approach might be simpler or more efficient.


