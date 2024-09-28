---
title: Iteration Examples
---

# {{ title }}

Let’s explore some examples that require the use of iteration, loops, in C#. Each example illustrates a different loop construct and its application.

## Example 1: Prime Numbers

This program calculates whether a given number is prime. A prime number is a positive integer greater than 1 that has no positive divisors other than 1 and itself. We can check if a number, `num`, is prime by dividing it by all integers between 2 and the square root of `num`. Here’s how the program works:

```csharp
using System;

namespace PrimeChecker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.Write("Enter a positive number: ");
            int num = int.Parse(Console.ReadLine());
            int divisor = 2;
            int maxDivisor = (int)Math.Sqrt(num);
            bool isPrime = true;
            
            while (isPrime && (divisor <= maxDivisor))
            {
                if (num % divisor == 0)
                {
                    isPrime = false;
                }
                divisor++;
            }
            Console.WriteLine($"Is {num} a prime number? {isPrime}");
        }
    }
}
```

**Explanation**

- **Lines 10-14**: Initialize variables and retrieve user input. We use the `sqrt` function from the `Math` library to determine the maximum divisor needed, which optimizes our checks.
- **Line 16**: The `while` loop checks two conditions: `isPrime` must remain `true`, and the current `divisor` should not exceed `maxDivisor`.
- **Line 18**: If the number is divisible by `divisor`, it is not prime, and `isPrime` is set to `false`.

!!! note
    The `break` operator can be useful for exiting the loop prematurely if needed.

## Example 2: Factorial Calculation

The factorial of a number `n`, denoted as `n!`, is the product of all positive integers from 1 to `n`. We can use a loop to calculate this:

```csharp
using System;

namespace FactorialCalculator
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.Write("Enter a value > ");
            ulong numIn = ulong.Parse(Console.ReadLine()); // Changed to ulong for larger input handling
            ulong n = numIn;
            ulong factorial = 1;

            do
            {
                factorial *= n;
                n--;
            } while (n > 0);

            Console.WriteLine($"{numIn}! = {factorial}");
        }
    }
}
```

**Explanation**

- The `do ... while` loop ensures that the calculation occurs at least once.
- We multiply `factorial` by the input value `n` and then decrement `n` until it reaches 0.
- The `ulong` type is used to accommodate larger numbers, but be aware that factorial values grow quickly and can lead to overflow. Consider using `BigInteger` from `System.Numerics` for very large values.

## Example 3: Approximation of a Square Root

In this example, we approximate the square root of a number using an iterative method. The loop uses `while(true)` to continuously refine the approximation until a specified accuracy is achieved:

```csharp
using System;

namespace Approximation
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.Write("Enter an integer value: ");
            int n = Convert.ToInt32(Console.ReadLine());
            double approximateValue = n / 2.0; // Use double for better precision
            Console.WriteLine($"Initial approximate value = {approximateValue}");

            while (true)
            {
                double betterValue = (approximateValue + n / approximateValue) / 2;
                if (Math.Abs(approximateValue - betterValue) < 0.001)
                {
                    Console.WriteLine($"Better value = {betterValue}");
                    break; // Exit the loop when sufficiently accurate
                }
                approximateValue = betterValue;
            }

            Console.Write("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

**Explanation**

- The `while(true)` loop continues indefinitely until the `break` condition is met.
- We use the formula `(approximateValue + n / approximateValue) / 2` to calculate a better approximation of the square root.
- The loop exits when the difference between the old and new approximations is less than `0.001`.

## Example 4: Using a For Loop

Here’s an example of using a `for` loop to print numbers from 1 to 10:

```csharp
using System;

namespace ForLoopExample
{
    class Program
    {
        static void Main(string[] args)
        {
            for (int i = 1; i <= 10; i++)
            {
                Console.WriteLine("Number: {0}", i);
            }
        }
    }
}
```

**Explanation:**

- The `for` loop initializes `i` to `1` and continues as long as `i` is less than or equal to `10`, incrementing `i` by `1` in each iteration.
- This concise structure is ideal for cases where the number of iterations is known.

