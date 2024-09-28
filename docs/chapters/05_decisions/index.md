---
title: Making Decisions
---

# {{ title }}

!!! note "In this chapter:"

    - Describe the term selection​
    - Learn to use relational operators and logical operators​
    - Write if…else if…else statements​
    - Use switch statements
    - Use flowcharts to describe and algorithm

In each of the short programs thus far each instruction has been executed __sequentially__, one after the other.  Each statement will alter the __state__ of the program so the order in which they are executed does matter.  This order is also known as the __flow of control__.  Designing the right algorithm to solve a problem is all about planning the steps needed to arrive at the solution, and ensuring those steps are _in the right order_.

This flow of control can be altered through the use of __selection__, __iteration__, __methods__ and __events__.  

In this chapter we will see how this flow of control can be changed using **selection**.  That is, either one statement (or block of statements) will be executed *or* another statement (or block of statements).

We will be making extensive use of the comparison operators from Chapter 3 (`<`, `>=`, `!=` etc.) as these are used in the __conditional statements__ that are used to determine the outcome of a decision.  Depending on the result of this decision (or condition), one path or another is followed in a program.  

For example, in the following extract, the `Console.WriteLine()` statement will only be executed if the value of the variable, `score`, is greater than or equal to $75$:

```cs
    if (score >= 75)
    {
        Console.WriteLine("Congratulations! You got an A*");
    }
```

Comparison operators can be used to compare expressions, such as two values, two expressions, or a number and a variable.[^expr]  The result will be a boolean value (true or false).  These expressions may also make use of one or more logical operators (AND, OR etc).

[^expr]: Not every pair of data types can be compared with each other directly e.g. you cannot compare a string to a number.
