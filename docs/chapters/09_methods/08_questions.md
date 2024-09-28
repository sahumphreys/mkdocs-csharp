---
title: Questions
---

# {{ title }}

1. Write method signatures for:

    - a method that takes one integer parameter
    - a method that returns a Boolean value
    - a method that takes one double and one string parameter and returns an integer value
    - a method that takes one integer reference parameter and returns a boolean value
2. Draw a hierarchy chart for the completed calculator program
3. What is meant by the term __structured programming__?
4. Explain how the two methods below can each use a variable named `x`.

    ```cs
    public void FirstMethod(int number)
    {
        int x = number;
    }
    public void SecondMethod()
    {
        int x = 0;
    }
    ```

5. What might be considered wrong with the following method?

    ```cs
    public void calcEverything(ref int a, ref int b, ref int c)
    {
        int total, avg;
        total = a + b + c;
        Console.WriteLine("the total of inputs = " + total);
        avg = total / 3;
        Console.WriteLine("the average of inputs = " + avg);
    }
    ```

## Additional Exercises

1. Create a method GetMax() with two integer (int) parameters, that returns the larger of the two numbers. Write a program that reads three numbers from the console and prints the biggest of them. Use the GetMax() method you just created.
2. Write a method that finds how many times a certain number can be found in a given array. Write a program to test that the method works correctly.
3. Write a program that calculates and prints the n! for any n in the range $1$ .. $100$.
4. Write a program to convert a $8$-bit binary number into its denary equivalent.  Decompose the program into several methods e.g. InputBinaryValue(), ConvertBit(), OutputResult().  Use the following pseudocode:

    ```cs
    Result = 0
    ColumnValue = 128
    PRINT "Enter a binary number to convert: "
    BinaryString <- INPUT
    FOR i = 0 TO (Length of BinaryString - 1)
        BitValue = 0
        IF (BinaryString[i] is a "1") THEN
            bitValue = bitValue + ColumnValue
        ELSE
            BitValue = bitValue
        END IF
        ColumnValue = ColumnValue /2
        Result = Result + bitValue
    END FOR
    PRINT Result
    ```

    - Test your program with the following values:  (a) 10000000; (b) 11111111; (c) 10010011
    - Adapt the program so it can work with any length of binary number
5. Write a program that solves the following tasks:

    - Put the digits from an integer number into a reversed order.
    - Calculate the average of given sequence of numbers.
    - Solve the linear equation a * x + b = 0.

    Create appropriate methods for each of the above tasks. Make the program show a text menu to the user. By choosing an option of that menu, the user will be able to choose which task to be invoked
