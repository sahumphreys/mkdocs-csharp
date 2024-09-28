---
title: Programming Task - Rock, Paper, Scissors
---

# {{ title }}

Here is an incomplete version of the game: Rock, Paper, Scissors.  It needs to be completed using an algorithm to determine the winner of the game.

```cs
using System;
namespace RockPaperScissors
{
    class RockPaperScissors
    {
        static void Main(string[] args)
        {
            string computerObject = "";
            int computerChoice = 0; ;
            bool computerWins = false;

            Random random = new Random();
            Console.Clear();
            Console.WriteLine("Enter your choice r(ock),p(aper),s(cissors): ");

            string userObject = Console.ReadLine();
            char userObjectFirst = userObject[0];           //what does this do?            
            computerChoice = random.Next(3);                // what does this do?

            //replace the following three if statements with a case statement
            if (computerChoice == 0) 
            {
                computerObject = "rock";
            }
            if (computerChoice == 1) 
            {
                computerObject = "paper";
            }
            if (computerChoice == 2) 
            {
                computerObject = "scissors";
            }

            Console.WriteLine("Computer choses " + computerObject);

            char computerObjectFirst = computerObject[0];               //what does this do?

            if (String.Equals(computerObjectFirst, userObjectFirst))    // what does this do?
            {
                Console.WriteLine("It's a draw");
            }                  
            else
            {
                //complete the missing logic to decide who has won
                if (computerWins == true)
                {
                    Console.WriteLine("Computer wins!");
                }
                else
                {
                    Console.WriteLine("You win!");
                }
            }
            Console.WriteLine("Press any key to quit ...");
            Console.ReadKey();
        }
    }
```
