---
title: Do.. While loop
---

# {{ title }}

The `do ... while` loop is similar to the `while` loop, but with a key difference: it guarantees that the loop body will execute at least once. Its syntax is as follows:

```csharp
do
{
    // body of the loop
} while (condition);
```

## Understanding the Do While Loop

In a `do ... while` loop, the **condition** is evaluated after the loop body has executed. This means that even if the condition is initially `false`, the code inside the loop will run once before the condition is checked. This characteristic makes the `do ... while` loop a **bottom-tested loop**.

### Example: Calculating the Average of a Series of Numbers

Let’s rewrite the previous example of calculating the average using a `do ... while` loop:

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

            do
            {
                Console.Write("Enter number (0 to quit) > ");
                value = Convert.ToDouble(Console.ReadLine()); // Changed to Convert.ToDouble for better precision
                if (value == 0)
                {
                    finished = true; // Ends the loop if the user enters 0
                }
                else
                {
                    count++; // Increment the count of valid entries
                    sum += value; // Add the entered value to the sum
                }    
            } while (!finished);

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

- **Loop Execution**: The `do ... while` loop starts by executing the code block. The user is prompted to enter a number, which is read and converted to a double for more accurate input.
- **Exit Condition**: If the user enters `0`, the `finished` variable is set to true, which will terminate the loop on the next evaluation. If the input is not zero, the program increments the `count` and adds the input value to `sum`.
- **Average Calculation**: After exiting the loop, the program checks if `count` is greater than `0` to avoid division by zero. If valid numbers were entered, the average is calculated and displayed. If no numbers were entered, an appropriate message is shown.


!!! warning
    Be sure to include a **semicolon** at the end of the `do ... while` loop. This is a common syntax requirement in C# and can lead to errors if omitted.
