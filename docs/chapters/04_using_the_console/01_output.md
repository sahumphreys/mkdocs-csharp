---
title: System.Console (Output)
---

# {{ title }}

In C#, reading from the keyboard and writing to the screen is accomplished using the `System.Console` namespace. This namespace provides numerous methods and properties for interacting with the console, facilitating both input and output operations.

## Console.Write and Console.WriteLine

We have used both `Console.Write()` and `Console.WriteLine()` to display content on the screen. The key difference between them is that `Console.WriteLine()` moves the cursor to the beginning of the next line after printing, whereas `Console.Write()` keeps the cursor at the end of the current line. Both methods accept a string argument to display on the screen.

The strings being printed can be concatenated using the `+` operator, allowing us to print data of different types within the same string. For example:

```cs
int age = 17;
Console.WriteLine("Peter is aged " + age + " years old");
```

This will print: `Peter is aged 17 years old`.

No casting or conversion is necessary when using the `+` operator for string concatenation. 

However, be cautious when concatenating values; make your intentions clear by using parentheses where necessary:

```cs
Console.WriteLine("Five: " + 2 + 3);    // Output: Five: 23
Console.WriteLine("Five: " + (2 + 3));  // Output: Five: 5
```

The `+` operator behaves differently depending on the data types of its operands. If both operands are numeric, it performs addition; if at least one operand is a string, it concatenates them into a single string.

### Formatting Output

We can provide both string literals, enclosed in double quotes, and variables in our output. There are several ways to embed these variables into strings. The choice of method is largely a matter of preference. For example:

```cs
string name = "Sally";
string town = "Heston";
int age = 17;
Console.WriteLine("{0} is from {1}, she is {2} years old", name, town, age);
```

In this statement, the output string includes numbered placeholders, followed by the corresponding variables. You can also specify the number of spaces for the variable output; for instance, `{0,10}` will print the first argument right-aligned in a space of 10 characters. To left-align, use a negative width specifier.

These placeholders can also be combined with **format specifiers**, which are letters followed by an optional precision value. Here are some examples:

```cs
Console.WriteLine("{0:C2}", 14.99); // Output: £14.99 (currency)
Console.WriteLine("{0:D8}", 19);    // Output: 00000019 (decimal)
Console.WriteLine("{0:E3}", 245);   // Output: 2.450E+002 (scientific notation)
Console.WriteLine("{0:X}", 255);    // Output: FF (hexadecimal)
Console.WriteLine("{0:P1}", 0.112);  // Output: 11.2% (percentage)
```

Alternatively, we can use **string interpolation** for formatting:

```cs
Console.WriteLine($"{name} is from {town}, she is {age} years old");
```

The `$` preceding the string indicates that it is an **interpolated string**. This syntax is more convenient and readable for creating formatted strings, and it is the preferred method in this text. The same format specifiers apply to interpolated strings.

### Formatting Dates

Dates can also be formatted in various ways. Here are some examples:

```cs
DateTime now = DateTime.Now;
Console.WriteLine(now);               // Output: 19/05/2021 16:25:07
Console.WriteLine("{0:D}", now);      // Output: 19 May 2021
Console.WriteLine("{0:Y}", now);      // Output: May 2021
Console.WriteLine("{0:d/MM/y}", now); // Output: 19/05/21
```

We can similarly use string interpolation for dates:

```cs
DateTime now = DateTime.Now;
Console.WriteLine($"{now:D}");              // Output: 19 May 2021
Console.WriteLine($"{now:Y}");              // Output: May 2021
Console.WriteLine($"{now:d/MM/y}");         // Output: 19/05/21
```
