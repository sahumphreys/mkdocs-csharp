---
title: Programming Task - Guessing Game
---

# {{ title }}

__The problem__: Write a program to get the computer to generate a random number between 1 and 100.  Set up a loop to keep inputting the guess.  If the guess is below the number then output "too low".  If the guess is above the number then output "too high".  Stop the program when the user guesses the number.

To implement this program we need to generate a random number.  We've seen this before in the Card game program but here's a reminder:

```cs
Random rnd = new Random();
int myRandomNumber = Rnd.Next(100)+1; 
```

The first statement looks unusual but it creates a new `object` called `random`.  This object has a number of built in methods for dealing with random numbers.  One of which is the `Next()` method.  This will return a random number between $1$ and $100$ in this instance.

!!! note From the syllabus
    AQA: Random number generation in a programming language (3.1.1.8/4.1.1.8):}
    
    - Be familiar with, and be able to use, random number generation
