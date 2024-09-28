---
title: Questions
---

# {{ title }}

1. Rewrite the following `if` statements into a single `if ... then ... else` statement:

    ```cs
    if (age < 18)
        ageCategory = "Junior";
    if (age >= 18)
        ageCategory = "Senior";
    ```

2. What is the output from the following code?

    ```cs
    int sum = 17;
    if (sum < 20)
        Console.Write("Under ");
    else
        Console.Write("Over ");
    Console.WriteLine("the limit");
    ```

3. Write an appropriate selection statement/construct to do the following:
    - If an integer variable `currentNum` is odd, change its value so it is now $3$ times the `currentNum` + $1$, otherwise change its value so that it is now half the value of `currentNum` (rounded down when `currentNum` is odd)
    - If an integer variable `n` has the value $1$, read in `double` values for `X` and `Y`, calculate and print their sum
    - Assign a value to a `double` variable `cost` depending on the integer variable `distance` as in the following table:

| Distance | Cost |
| -------- | ---- |
| 0 through 100 |  5.00 |
| More than 100 but not more than 500 | 8.00 |
| More than 500 but less then 1,000 | 10.00 |
| 1,000 or more | 12.00 |

## Additional Exercises

1. Write an if-statement that takes two integer variables and exchanges their values if the first one is greater than the second one.
2. Write a program that asks for a digit (0-9), and depending on the input, shows the digit as a word (in English) using a switch statement.
3. A year is a leap year if it is divisible by 4, unless it is a century year, in which case it is only a leap year if it is divisible by 400 (e.g. 2000 is a leap year, but 1900 was not).  Design and write a program to accept a year and output a message indicating if it is a leap year.
4. (something to stretch the Maths muscles ...) Write a program that gets the coefficients $a$, $b$ and $c$ of a quadratic equation: $ax^{2} + bx + c$, calculates and prints its real roots (if they exist).

    !!! tip
        A quadratic equation may have one or two real roots or no real roots at all. In order to calculate the real roots of a given quadratic equation, we first calculate the discriminant ($D$) by the formula: $D = b^{2} - 4ac$. If the discriminant ($D$) is zero, then the quadratic equation has one double real root and it is calculated by the formula: $x_{1,2} = \frac{-b}{2a}$.  If the value of the discriminant is positive, then the equation has two distinct real roots, which are calculated by the formula:
        $x_{1,2} = \frac{-b \pm \sqrt{b^2-4ac}}{2a}$. If the discriminant is negative, the quadratic equation has no real roots). Quadratic equations may have 0, 1 or 2 real roots.  The `Math` namespace has a square root method: `Math.Sqrt()`.

5. READ and DO the [tutorial on iteration](https://csharp.net-tutorials.com/control-structures/loops/)
