---
title: Questions
---

# {{ title }}

1. An array has been created to store test marks:

        | [0] | [1] | [2] | [3] | [4] | [5] | [6] |
        |-----|-----|------|----|-----|-----|-----|
        | 32  |  65 |  59  | 23 |  71 | 47  | 63  |

    a. What is the value contained in index [3]?

    b. How many indices does the array have?

    c. What is the index for the value 65?

    d. The marks for [2] gets changed to 58 following a remark.  Write the C\# statement to make this change.

2. A 2D array, `marks`, stores the marks achieved by students in a recent exam:

    || [0] | [1] | [2] | [3] | [4] | [5] | [6] |
    |---|-----|-----|------|----|-----|-----|-----|
    |Programming Test| 32  |  65 |  59  | 23 |  71 | 47  | 63  |
    |Theory Test | 38 | 52 | 65 | 32 | 71 | 49 | 70 |

    a. What is the value contained in `marks[2,3]`?

    b. How many values can be stored in this array?

    c. What is the index reference for the value $49$?
    
    d. The mark in student [3] in their programming test has been entered incorrectly, write the C\# statement to update this mark to $33$

3. Study the following code[^code]:

    ```cs
    int n = 78;
    int r;
    Console.Write("Enter an integer: ");
    n = Convert.ToInt32(Console.ReadLine());
    string op = "";
    while (n > 0)
    {
        r = n % 2;
        n = n / 2;
        op = r + op;
    }
    Console.WriteLine(op);
    ```

    a. Complete a trace table for this code with the input value 47

    b. What does the code do?

[^code]: Adapted from [A Level WikiBooks](https://en.wikibooks.org/wiki/A-level_Computing/AQA/Problem_Solving,_Programming,_Data_Representation_and_Practical_Exercise/Problem_Solving/Trace_tables_)

## Additional Exercises

1. Write a program, which creates an array of 20 integer elements.  Each element should be initialised with a value equal to the square of its index.  Print the elements to the screen.
2. Write a program to read in the contents of a $10$ element array, then prints them to the screen in reverse order of entry.
3. Write a program that initialises an array of 20 elements with random integers ($0 <= n >= 100$).  Ask the user for an integer and search the array to discover if their number is in the array.
4. Write a program to read 20 integers from the user and sort the even and odd numbers into two separate arrays and print the results to the screen
5. Write a program to merge two arrays of the same size sorted in ascending order into a new array
6. Write a program to print to the screen a multiplication table (1-12)
7. Write a program to read elements of two matrices (2D arrays) and add elements of each matrix.  Print the result to the screen.
8. There are lots of different sorting algorithms.  Research the selection sort, and the insertion sort.  Write programs to implement both of these sorting algorithms.
9. Write a program that lists all prime numbers between 1 and a given value.  Use a List to store the results (as we don't know how many prime numbers there might be)
