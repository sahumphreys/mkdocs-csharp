---
title: Methods
---

# {{ title }}

!!! note "In this chapter"
    - Describe the terms __subroutine__, __method__, __procedure__ and __function__
    - Define and call your own subroutines
    - Use __parameters__ and __arguments__ to pass values to a subroutine
    - Use __return__ statements to return values back to the function call
    - Know the difference between __passing by value__ and __passing by reference__
    - Know the difference between __local__ and __global__ variables
    - Identify advantages of using subroutines​

As the problems we want to solve get larger, and presumably harder, it makes sense to split the algorithm into smaller sub-problems.  When taken separately these smaller sub-problems are easier to solve and if we solve all the sub-problems we'd have solved the larger one!  This is a process of breaking a larger problem into a set of smaller sub-problems is known as __decomposition__.

Each sub-problem can have its own section in our code taking responsibility for handling just that part of the problem.  These sections are known as __subroutines__, or __methods__ in C\#.  You'll also encounter the terms __procedure__ and __function__.  These terms _do_ have a specific meaning as we'll see in this chapter as a method can be _either_ a procedure or a function:

- __function__: functions __return__ a value to where the function was __called__
- __procedure__: does not return a value

There are very good reasons to use methods in our program code:

- The code will be structured better
- The code will be more readable
- Duplication will be kept to a minimum (__Don't Repeat Yourself (DRY)__ is a good maxim to adopt)
- Code can be re-used

Of course, we have already used a method, all the code examples we've looked at thus far had a `Main()` method.  This is the entry point to our programs, it is the _main_ method in the Program _class_.

!!! note "From the syllabus"
    AQA: Subroutines (procedures/functions) (3.1.1.10/4.1.1.10)}
    
    - Be familiar with subroutines and their uses. Know that a subroutine is a named 'out of line' block of code that may be executed (called) by simply writing its name in a program statement. Be able to explain the advantages of using subroutines in programs
