---
title: While loop
---

# {{ title }}

The `while` loop is one of the simplest and most commonly used control structures in programming. Its syntax is as follows:

```csharp
while (condition)
{
    // body of the loop
}
```

## Understanding the While Loop

In this context, the **condition** is any expression that evaluates to a **Boolean** result, meaning it can be either `true` or `false`. The loop will continue to execute as long as the condition remains `true`. Once the condition becomes `false`, the loop terminates. It's important to note that if the condition is initially `false`, the loop body will not execute at all. This characteristic distinguishes the `while` loop from the `do ... while` loop, which guarantees at least one execution of the loop body.

### Example: Calculating the Average of a Series of Numbers

Let’s look at a practical example where we use a `while` loop to calculate the average of a series of numbers. 

```csharp
// Design an algorithm and write a program to find the average of a series of numbers.
using System;

namespace AverageCalculator
{
    class Program
    {
        static void Main(string[] args)
        {
            double average;
            double sum = 0;
            double value;
            int count = 0;
            bool finished = false;

            while (!finished)
            {
                Console.Write("Enter number (0 to quit) > ");
                value = Convert.ToDouble(Console.ReadLine()); // Changed to Convert.ToDouble for more accurate inputs
                if (value == 0)
                {
                    finished = true; // Ends the loop if the user enters 0
                }
                else
                {
                    count++; // Increment the count of valid entries
                    sum += value; // Add the entered value to the sum
                }
            }

            if (count > 0) // Check to avoid division by zero
            {
                average = sum / count; // Calculate the average
                Console.WriteLine($"Average = {average}");
            }
            else
            {
                Console.WriteLine("No numbers were entered to calculate an average.");
            }

            Console.Write("Press any key to quit ...");
            Console.ReadKey();
        }
    }
}
```

**Code Explanation**

- **Lines 14, 16**: The `finished` Boolean variable acts as the condition for the loop. The loop will continue to run as long as `finished` is **not** true.
- **Line 22**: When the user enters `0`, `finished` is set to true, terminating the loop. If the input is non-zero, the program increments the `count` and adds the input value to `sum`.
- **Line 30**: Once the loop ends, the average is calculated using `sum` divided by `count`. A check is included to ensure that at least one valid number was entered to avoid division by zero.

!!! note
    If the condition is `false` when the loop is first encountered, the loop will not execute at all. This property makes the `while` loop a **top-tested loop**, as the condition is evaluated before each iteration.

## Alternative Exit Conditions

An alternative approach could involve asking the user for the total number of values to be averaged. In this case, the loop would need a counter variable to track how many numbers have been entered, allowing it to terminate gracefully once the specified number is reached.
