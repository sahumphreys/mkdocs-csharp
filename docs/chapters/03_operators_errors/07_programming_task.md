---
title: Programming Task - Pick a Card
---

# {{ title }}

This problem will give you practice in using a range of variable types and the arithmetic operations you can perform on them.

The problem:

__Write a program that will display the rank and suit of a card chosen randomly from a standard pack.__

You are provided with an incomplete Card Game program (code below).

It already includes the statement to generate a random number and some incomplete code to output the rank and suit for the card.

Your tasks are to:

- add in the operations to generate the rank and suit of the card (this is the part that uses $\%$ and $/$)
- complete the selection (`if` and `case`) statements (you can read about these in the next chapter)
- test your algorithm by running the program, revising the algorithm where necessary

```cs
using System;

namespace CardGameIncomplete
{
    public class CardGameIncomplete
    {
        public static void Main(string[] args)
        {
            int number, ranknum, suitnum;
            string rank = "";
            string suit = "";

            // "seeds" (initialises) the random number generator
            Random random = new Random();

            //selects a random number between 0 and 51,
            //adds one to it and assigns the result to number
            number = random.Next(52) + 1;

            // ???  complete this 
            ranknum =
            suitnum =

            // ??? complete this case statement for the other ranks
            switch (ranknum)
            {
                case 1:
                    rank = "Ace";
                    break;
                case 2:
                    rank = "Two";
                    break;
                case 3:
                    rank = "Three";
                    break;
            }

            // add if statements for the other suits
            if (suitnum == 0)
            {
                suit = "Clubs";
            }
            // output using an interpolated string
            Console.WriteLine($"Your card is the {rank} of {suit}”);
            Console.ReadKey();
        }
    }
}
```

## Extension Tasks

(These require the use of loops and are optional. You can find out how to use loops by looking further ahead in the text)

1. Add code to enable a user to "Pick a Card", add exception handling to this block of your program
2. Extend the program so that it repeatedly chooses a random card until the user enters 'q'
3. Extend the program so that it shows every card in a standard pack in order from the two of clubs to the ace of spades.

!!! tip
    __HINT__: Adding these extensions to the same program will produce a lot of repetition.  Either, read ahead and look up how to implement a method, or use three separate projects

4. Look up the Unicode representation for suits of cards and adapt your program to print those to the console rather than the word "Spades" or "Hearts" etc..
