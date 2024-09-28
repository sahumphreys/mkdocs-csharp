---
title: Thinking Recursively
---

# {{ title }}

Recursion can be challenging because we're often more comfortable thinking iteratively. When faced with problems that require looping, we naturally gravitate towards constructs like `for` and `while`. This guide will help you rethink such problems using recursion, a different but powerful approach to problem-solving in programming.

We'll use a simple problem—summing the digits of an integer—to illustrate the steps to move from an iterative to a recursive solution e.g. $245$ sums as $11$, $9764523$ sums as $36$.

## Step 1: Create the Iterative Solution

This should be a straightforward exercise:

```cs
Console.Write("Enter an integer: ");
string numStr = Console.ReadLine();
int sum = 0;
for (int i = 0; i < numStr.Length; i++)
{
    sum += numStr[i] - '0'; // using '0' instead of 48 for clarity
}
Console.WriteLine(sum);
```

## Step 2: Write it as a Function

We can turn this code into a function by passing the string representation of the number as a parameter and returning the sum. This helps us encapsulate the functionality and makes the code more reusable.

```cs
// from Main()
Console.Write("Enter an integer: ");
numStr = Console.ReadLine();
Console.WriteLine(GetSumOfDigits(numStr));
//

static int GetSumOfDigits(string numStr)
{
    int sum = 0;
    for(int i = 0; i < numStr.Length; i++)
    {
        sum += numStr[i]-48;
    }
    return sum;
}
```

## Step 3: Identify the Minimal Problem Instance

The minimal problem instance, or base case, is when the number has only one digit. For instance, if the number is `5`, then the sum is simply `5`. The base case in a recursive solution provides a stopping point to avoid infinite recursion.


## Step 4: Amend the Function for the Base Case

Our function will loop even when num is $5$.  This needs to be amended to cope with this instance, ensuring that when the input length is $1$ just return that number:

```cs
static int GetSumOfDigits(string numStr)
{
    if (numStr.Length == 1)
    {
        return numStr[0] - '0'; // base case: return single digit
    }
    // Iterative approach for now, will be replaced in the next step
    int sum = 0;
    for (int i = 0; i < numStr.Length; i++)
    {
        sum += numStr[i] - '0';
    }
    return sum;
}
```

## Step 5: Apply Recursion to the Function

We already have our base case, when the string length is `1`. Now, we need to think about breaking the problem into smaller sub-problems. For example, summing the digits of `245` can be thought of as `2 + GetSumOfDigits("45")`; and the sum of "45" is the same as 4 + GetSumOfDigits("5"); and we know GetSumOfDigits("5"); is $5$.

So, we need to pass back into our function the rest of the string that has not yet been handled knowing it will terminate when there is a single digit to process.

There is a "gotcha" here that needs more unpacking, how to pass back a shorter string to our function?  In C\# a string, under the hood, is an zero-based index array of characters and has a method returning the length of the string.  Thus, "5" will have a length of $1$ and to access the value we'd use numStr[numStr.Length - 1];.  This is fiddly, it's simpler to pass in to our function an additional parameter, the length of the string:  GetSumOfDigits(string num, int length);.  
In each recursive call, we process one digit and pass the rest of the string to the next call until we reach the base case.

```cs
static int GetSumOfDigits(string numStr, int length)
{
    if (length == 0)
    {
        return 0; // base case: when there are no more digits left
    }
    // Recursively add the last digit and reduce the length
    return (numStr[length - 1] - '0') + GetSumOfDigits(numStr, length - 1);
}
```

Our main function can then be used to call this function:

```cs
Console.Write("Enter an integer: ");
string numStr = Console.ReadLine();
int result = GetSumOfDigits(numStr, numStr.Length);
Console.WriteLine(result);
```

**Exercise:** Using the steps outlined above, try writing a recursive function that calculates the power of a number. For example, `3^4 = 3 * 3 * 3 * 3 = 81`. Think about the base case and how you can reduce the problem with each recursive call.
