---
title: Questions
---

# {{ title }}

## Sum numbers in an array - trace table

Complete the trace table for the following program. How many times is the recursive routine called? What is output?

```cs
int marks[] = { 3, 6, 2, 8 };
int sum = GetSumRecursively(marks, marks.length);
Console.WriteLine(COnvert.ToInt32(sum));

static int GetSumRecursively(int[] numbers, int length)
{
    if (length == 0)
        return 0;
    else
    {
        return GetSumRecursively(numbers, length-1) + numbers[length-1];
    }
}
```

| Numbers | length | numbers[0] | output |
| ------- | --------------- | -----------| -------|
| {3,6,2,8} | 4 | 3 + addNums({6,2,8}) | |
| {6,2,8} | |||
|||||
||||8|
|||||
|||||

## Additional Exercises

1. Write a recursive function to return the length of a string
2. Write a function that takes a string as a parameter and returns a new string that is the reverse of the old string. (Hint: use `substring` method on the string to pass a smaller form of the string.)
3. Write a program to calculate the power of any number using recursion e.g. `MyPow(x, n)` that returns $x^n$.
4. Write a recursive function that returns true if an input string is a palindrome e.g. "rotor" is a palindrome, it can be read forwards and backwards.  (Hint:  the start and end letters must be the same, the second and penultimate letters must be the same, and a single character is a palindrome).
5. Write a program that solves the Towers of Hanoi problem (see [https://www.educative.io/edpresso/what-is-the-tower-of-hanoi-problem](https://www.educative.io/edpresso/what-is-the-tower-of-hanoi-problem))
