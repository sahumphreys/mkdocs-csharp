---
title: System.Console (Input)
---

# {{ title }}

The keyboard is the standard input device in C#, and the `System.Console` class provides the method `Console.ReadLine()` for reading user input.

When `Console.ReadLine()` is called, the system waits for the user to type something on the keyboard. The entered data can be assigned to a variable or ignored:

```cs
Console.WriteLine("Enter your name: ");
string name = Console.ReadLine();               // Data entered is assigned to a variable
Console.WriteLine($"Hello {name}");
Console.WriteLine("Press any key to quit...");
Console.ReadLine();                             // Data entered is ignored
```

Data entered through the keyboard is always treated as a string. If you need the data to be numeric, it must be converted before any processing can be performed. As mentioned earlier, there are two common approaches for this conversion:

- Using `int.Parse()` or `int.TryParse()`
- Using `Convert.ToInt32()`

If you're reading data from a trusted source (e.g., when you expect to read an integer), using `Parse()` is generally safe. However, if you're getting the data from a user, it's advisable to use `TryParse()` to avoid exceptions.

Here are examples of both methods for reading numeric input:

```cs
Console.WriteLine("Enter your age: ");
int age = int.Parse(Console.ReadLine()); // Using Parse

// or

Console.Write("Enter your age: ");
int age1 = Convert.ToInt32(Console.ReadLine()); // Using Convert
```

!!! note
    There is very little difference in behavior between `Convert` and `Parse()`. However, it's worth mentioning that `Convert.ToInt32()` will return `0` if the argument is `null`. 

Be aware that exception errors may still occur during conversion and should be handled appropriately.

If you're only expecting a single key to be input (for example, when displaying a prompt like "Press any key to continue..."), you can use `Console.ReadKey()` instead:

```cs
Console.WriteLine("Press any key to continue...");
Console.ReadKey(); // Waits for a key press
```
