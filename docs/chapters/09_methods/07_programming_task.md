---
title: Programming Task - Calculator
---

# {{ title }}

Write a calculator program that inputs two numbers, asks the user what calculation they want to perform and then outputs the result.  Each calculation should be performed and output from inside it's own procedure.  The code below should help you get started.

- Modify the program so it can also perform subtraction, multiplication, and division, use either procedures or functions for each method
- Add a loop so that the menu repeats until the user wants to quit
- __Challenge 1__: Include procedures for floor (i.e. integer) division and modulus
- __Challenge 2__: Use exception handling with all of the user inputs (or write methods to `GetInt()` and `GetFloat()` with validation)
- Modify the methods, converting them from procedures into functions

```cs
using System;

namespace Calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Welcome to the calculator program\n");

            // Ask the user for two number and store them as floats
            Console.Write("Enter the first number: ");
            float number1 = float.Parse(Console.ReadLine());

            Console.Write("Enter the second number: ");
            float number2 = float.Parse(Console.ReadLine());

            // Output the menu options
            Console.WriteLine("\nEnter the menu number of the calculation to perform: ");
            Console.WriteLine("1 - Addition");
            Console.WriteLine("2 - Subtraction");
            Console.WriteLine("3 - Multiplication");
            Console.WriteLine("4 - Division\n");

            // Ask for the menu option
            string menuOption = Console.ReadLine();

            // Perform a subroutine based on the menu option
            if (menuOption == "1")
            {
                Addition(number1, number2);
            }
            else
            {
                Console.WriteLine("Please choose a valid option");
            }
        }

        // The addition procedure has two floats as parameters, adds them together and outputs the result
        static void Addition(float num1, float num2)
        {
            Console.WriteLine("\nThe result is: " + (num1 + num2));
        }
    }
}
```

### Secret Word

[From ZigZag Education C# Console Programming]

Create a new project called SecretWord and copy the code from below into your project. Adapt the program so that there are separate procedures and functions for:

- Outputting the menu (a procedure)
- Guessing the secret word (a procedure with a parameter)
- Changing the secret word (a function)
- Quitting the program (a procedure)

```cs
using System;

namespace SecretWord
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialise the variables and secret word
            string menuOption;
            string guess;
            string secretWord = "Computer";

            do
            {
                // Output the menu
                Console.WriteLine("\nWelcome to the guessing program menu - choose your option:");
                Console.WriteLine("1 - Change the secret word");
                Console.WriteLine("2 - Make a guess");
                Console.WriteLine("3 - Quit");

                // Ask the user for the menu number
                menuOption = Console.ReadLine();

                // Choose a task depending on the menu option 
                switch (menuOption)
                {
                    case "1":
                        // Change the secret word
                        Console.WriteLine("What is the new secret word?");
                        secretWord = Console.ReadLine();
                        break;
                    case "2":
                        // Guess the secret word
                        Console.WriteLine("Guess the secret word:");
                        guess = Console.ReadLine();

                        // Check whether the word entered was the secret word
                        if (guess == secretWord)
                        {
                            Console.WriteLine("Well done - you have guessed the secret word!");
                        }
                        else
                        {
                            Console.WriteLine("Sorry, that is not the secret word");
                        }
                        break;
                    case "3":
                        // Quit the program
                        Console.WriteLine("Thank you for playing secret word");
                        Environment.Exit(0);
                        break;
                    default:
                        Console.WriteLine("Invalid menu choice");
                        break;
                }
            }
            while (menuOption == "1" || menuOption == "2");
        }
    }
}
```
