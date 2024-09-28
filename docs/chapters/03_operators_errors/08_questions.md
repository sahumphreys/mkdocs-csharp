---
title: Questions
---

# {{ title}}

A primary school teacher wants a program to test their pupils' knowledge of times tables (2 - 12).  Read through the code for this problem and answer the following questions.

```cs
using System;

namespace timesTable
{
    class Program
    {
        static void Main(string[] args)
        {
           const int NUM_OF_QUESTIONS = 10;
            const int LOWER = 2;
            const int UPPER = 12;
            string name;
            int correct = 0;

            Console.Clear();
            Console.WriteLine("Test: Times Tables");

            Console.Write("What is your name? ");
            name = Console.ReadLine();

            Random rnd = new Random();
            for (int i = 1; i <= NUM_OF_QUESTIONS; i++)
            {
                int first = rnd.Next(LOWER,UPPER);
                int second = rnd.Next(LOWER,UPPER);
                int answer = first * second;
                Console.Write($"{i} : {first} * {second} = ");
                int myAnswer = Convert.ToInt32(Console.ReadLine());
                if (answer == myAnswer)
                {
                    correct++;
                    Console.WriteLine($"Correct! {correct}/{i}");
                }
                else
                {
                    Console.WriteLine($"The correct answer was {answer} ({correct}/{i})");
                }
            }
            Console.WriteLine($"{name}, you scored {correct}!");
            Console.Write("Press any key to quit ...");
            Console.ReadKey();
        }
    }
}
```

1. Why is it a good idea to use a constant for the number of questions being asked?
2. How are constants different from variables?
3. Explain, with reference to the code, how a random number is being generated.
4. The program uses a loop (see chapter 6).  Can you explain how this loop works?
5. Explain the line `correct++`
6. Modify the code to output the percentage of correct answers
7. Explain what is meant by exception handling, how and where might exception handling be used in this program?

## Additional Exercises

1. Using a bitwise operator write a program that checks if an integer is odd or even.  
2. The gravitational field of the Moon is approximately 17% that of the Earth.  Write a program that calculates your weight on the Moon.  
3. Write a program that takes as input a four digit number and calculates the sum of the digits
4. EXTENSION: Write a program that checks if a given number input from the keyboard is a prime number.  (This requires a loop.)
