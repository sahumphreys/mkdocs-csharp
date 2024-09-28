---
title: Strings, Encryption, and Testing
---

# {{ title }}

!!! note "In this chapter"
    - Declaring, creating, and initializing a string data type.
    - Implementing some of the common __string handling methods__ used in C#.
    - Introduction to __regular expressions__.
    - Rudimentary __encryption__ using the __Caesar Cipher__.
    - How to __dry-run__ a program using a __trace table__.

A string in C# is a sequence of characters (`char`) stored in memory. While the `char` data type is used for a single character, we use the `string` data type for a sequence of characters. 

As discussed in Chapter 4 ("Using the Console"), each character in .NET is represented using a numeric value from the __Unicode__ standard. Unicode succeeded ASCII as the default for character representation. ASCII uses a single byte to represent common English characters and symbols, but it is too limited for non-English alphabets and additional symbols. Unicode, in .NET, uses a 16-bit code, providing 65,535 different available characters.

Although we could theoretically create an array of `char` with a specified length, it would be static and require manual processing for each character. While there are some situations where arrays of `char` are necessary, C# provides the `String` class, which is used more frequently due to its flexibility and ease of use.

One important aspect of the `String` class is that it is __immutable__, meaning that its contents cannot be altered after it is created. Instead, if we try to change a string, a new string object is created in memory:

```cs
string name = "Peter";
name[0] = 'S';          // This line will cause a compilation error
name = "Sally";         // A new string "Sally" is created, and name now refers to it
Console.WriteLine(name); // Outputs: Sally
```

Internally, a string is represented as an array of characters, allowing individual access to its elements using indices:

```cs
string myString = "Hello, World!";
Console.WriteLine(myString.Length);     // Outputs: 13
Console.WriteLine(myString[0]);         // Outputs: 'H'
```

!!! note "From the syllabus"
    AQA: String-handling operations in a programming language (3.1.1.7/4.1.1.7)

    - Be familiar with and be able to use: length, position, substring, concatenation, character to character code, character code to character, string conversion operations.
