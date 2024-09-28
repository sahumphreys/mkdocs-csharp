---
title: Extended Theory - Random Number Generation
---

# {{ title }}

Following the in-depth exploration of binary in the last chapter, this section will briefly consider random numbers. While one might get sidetracked by philosophical questions about the nature of randomness, what we seek when generating a sequence of random numbers is for each value to be produced by chance, independent of any other numbers in the sequence. A common application of this concept can be found in our "Pick a Card" program, where we need the program to select one of the 52 cards. When we run it again, we would generally expect a different card to be selected.

The topic of random number generation has a long history, and today there are two primary approaches:

- **True Random Numbers**
- **Pseudo Random Numbers**

The "Pick A Card" program relied on a random number generator class built into C#. This class is a **pseudo-random number generator**, meaning it relies on an algorithm to produce random numbers. The algorithm requires a **seed** value; using the same seed will generate the same set of random numbers. Therefore, if you know the seed and the algorithm used, you can reproduce the seemingly random results. For most applications, this approach is sufficient. However, when generating a seed for encrypting sensitive information, such as credit card details, a stronger method is needed. C# addresses this with the `RNGCryptoServiceProvider` class.

For reference, the algorithm used by the `Random` class in C# is a **subtractive random number generator**, with the seed derived from the system clock.

To generate **true random numbers**, specialized additional hardware is required to read environmental noise or some other physical phenomenon that is inherently random.

While it is unlikely you will need to write your own random number generator, understanding some of the underlying issues can be beneficial:

```cs
static int RandomSeed(int n, int m, int a)
{
    return n = m * n % a; 
}
```

In this code snippet, we define a **function** that returns an `int` value and accepts several **parameters** in the parentheses following the function name. We will explore methods in more detail in Chapter 9.

This function takes an input value `n`, multiplies it by `m`, and returns the remainder after dividing by `a`. Thus, the value of `a` determines our range. For example, if `a = 11`, our range will be between 1 and 10. We can use this function to generate a sequence of 10 random numbers, where each successive number is derived from the previous one:

```cs
static void Main(string[] args)
{
    int start = 1;
    for (int i = 0; i < 10; i++)
    {
        int n = RandomSeed(start, 7, 11);
        Console.Write(n + " ");
        start = n;
    }
}
// Example Output: 7 5 2 3 10 4 6 9 8 1
```

In our `Main()` method, we use a loop to generate 10 values. We will cover loops in more detail in Chapter 6.

The output from this loop appears random, as there is no immediately obvious pattern in the generated values. However, if we run it again with the same seed, we will get the exact same sequence of values. Note also how we use the previous value to generate the next number in the sequence, thus passing the **state**.

However, this method is relatively weak because we can begin to predict the next number based on the preceding ones. To improve this, we can introduce a value outside the specified range and then apply the modulo operator to ensure the result falls within our desired range:

```cs
static void Main(string[] args)
{
    int start = 1;
    for (int i = 0; i < 10; i++)
    {
        (int n, int state) = RandomSeed(start, 7, 101, 10);
        Console.Write($"({n},{state}) ");
        start = state;
    }
}

static (int, int) RandomSeed(int n, int m, int a, int b)
{
    int j = m * n % a;
    return ((j - 1) % b + 1, j); 
}
```

In this example, we return two values, utilizing a **tuple**. The first value represents our random number in the range of 1 to 10, while the second value serves as the revised state for our intermediate value. The output will appear as follows:

```bash
(7,7) (9,49) (10,40) (8,78) (1,41) (5,85) (10,90) (4,24) (7,67) (5,65)
```

The first value in each pair is part of our random number sequence. The generator now selects some previously used values, making it harder to predict the next number in the sequence. This unpredictability increases significantly if we utilize a much larger prime number than 101.

Before concluding our discussion on random number generation, it’s important to address one further issue: if a program depends on random numbers, testing becomes more challenging, as the expected values are unknown. The solution is straightforward: set the seed for the random number generator so that each sequence of values remains consistent across runs.

When using the `Random()` class in C#, we can specify the seed value during initialization:

```cs
Random rnd = new Random(100);
int a = rnd.Next(0, 10);
int b = rnd.Next(0, 10);
Console.WriteLine(a);
Console.WriteLine(b);
```

Running this program multiple times will produce the same values for `a` and `b`. Once testing is complete, remove the seed parameter and allow C# to choose the seed value based on the system clock.
