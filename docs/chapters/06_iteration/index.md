---
title: Iteration
---

!!! note "From the syllabus"
    AQA: Use, understand and know how the following statement types can be combined in programs; Use definite and indefinite iteration, including indefinite iteration with the condition(s) at the start or the end of the iterative structure. A theoretical understanding of condition(s) at either end of an iterative structure is required (3.1.1.2/4.1.1.2):}
    
    - Often in an algorithm, a group of statements needs to be executed again and again until a certain condition is met, this is iteration.

Programming often requires a series of statements to be repeated.  These statements may be repeated a fixed number of times or will execute until a particular condition is reached (or not execute at all if the condition fails).  These loop constructs are one of the most important constructs to master and a key feature of algorithm design.  

Many program errors are caused by poorly constructed loops.  If the loop never ends we enter an __infinite loop__, thus the key feature to remember when designing a block of statements that repeat, or loop, is the exit strategy: __when should the loop terminate__?


There are two types of loop:

- __for loops__: when the number of iterations (repetitions) is pre-determined, also known as __counted loops__, or __count controlled loops__
- __while loops__: when the number of repetitions is not predetermined, or __conditional loops__, or __condition controlled loops__


For example, consider the following problem:

_Design an algorithm and write a program to find the average of a series of numbers._

We'll illustrate solutions to this problem with each of the three different types of loop structure available in C\# in the following sections.
