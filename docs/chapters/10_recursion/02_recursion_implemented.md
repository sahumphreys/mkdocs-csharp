---
title: Implementing Recursion
---

# {{ title }}

Let's continue analyzing our `PrintValues()` example:

```cs
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

To understand how this function works, it's helpful to trace the flow of execution step-by-step. Using the values `a = 4` and `b = 6`, the series of calls to the `PrintValues()` method would look like this:

```cs
PrintValues(4, 6):
    Console.Write(4);
    PrintValues(5, 6):
        Console.Write(5);
        PrintValues(6, 6):
            Console.Write(6);
            return;
        return;
    return;
```

## Understanding Recursive Algorithms

Recursive algorithms generally have the following components:

- **Base Case**: This is the simplest version of the problem, where the solution can be directly obtained without further recursion. The base case is crucial because it provides a stopping condition to prevent infinite recursion. In our example, the base case is:

    ```cs
    if (a == b) { ... }
    ```
    Here, the function stops calling itself when `a` is equal to `b`.

- **Recursive Call**: This is where the function calls itself with a modified version of the original problem, bringing it closer to the base case. It is essential to ensure that each recursive call makes progress towards the base case. In our example:

    ```cs
    PrintValues(a + 1, b)
    ```
    Each call increments `a`, moving closer to the base case.

- **Processing (Work)**: This is the part of the function that performs any required computation before or after the recursive call. In our example:
    ```cs
    Console.Write($"{a}, ");
    ```

## The Role of the Stack

The stack, as discussed in the previous chapter, plays a crucial role in the execution of recursive methods. Each time the method is called, its current state—return address, parameters, and local variables—is pushed onto the stack[^stack]. This ensures that when the function returns, it can continue where it left off.

For instance, when `PrintValues(5, 6)` is called, it is pushed onto the stack, followed by `PrintValues(6, 6)`. Once the base case is reached, these calls are popped off the stack in reverse order, completing one after the other. This is known as the _unwinding_ of the recursive calls. The stack operates as a Last In, First Out (LIFO) structure.

[^stack]: The stack is an area of memory that stores local variables and function calls. It follows a __Last In, First Out__ (LIFO) order, meaning the last method pushed onto the stack is the first one to be popped off.

## Another Example: The `Enigma` Method

Consider the following method, which also demonstrates the components of a recursive function:

```cs
static void Enigma(int n)
{
    if (n < 0)
    {
        Enigma(-n);
    }
    else if (n < 10)
    {
        Console.Write(n);               
    }
    else
    {
        Enigma(n / 10);                 
        int x = n % 10;                 
        Console.Write(", {0}", x & 1);
    }
}
```

### Exercise: Tracing the `Enigma` Method

Work through the following calls to the `Enigma()` method and predict what will be displayed on the screen:

- `Enigma(4)`
- `Enigma(99)`
- `Enigma(123)`
- `Enigma(-3456)`
- `Enigma(1234567)`

Let's trace `Enigma(99)` step-by-step:

1. `99` is neither negative nor less than `10`, so the final `else` block is executed.
2. The method calls itself with `Enigma(99 / 10)`, which is `Enigma(9)`. This call is pushed onto the stack, and the first call remains unfinished.
3. `9` is less than `10`, so `9` is printed to the screen, and the method returns.
4. Control returns to the previous call where `n = 99`. Now, `x` is set to `99 % 10`, which is `9`, and `9 & 1` evaluates to `1`. This `1` is printed to the screen.

Try repeating this process with the other test calls listed above. Check that you understand why the output for these calls is:

- `Enigma(4)` prints `4`
- `Enigma(99)` prints `9, 1`
- `Enigma(123)` prints `1, 0, 1`
- `Enigma(-3456)` prints `3, 0, 1, 0`
- `Enigma(1234567)` prints `1, 0, 1, 0, 1, 0, 1`

## When to Use Recursion

This brings us to the question: Which implementation is _better_? Is recursion always the best solution compared to an iterative one?

Recursion can simplify code and make certain problems easier to solve, especially those involving complex data structures like trees. However, it also uses more memory due to the overhead of multiple function calls and can lead to stack overflow if not carefully managed.

It's not the best solution for all problems, but for some cases (as we will see later in the chapter), recursion is precisely the right tool to use.

