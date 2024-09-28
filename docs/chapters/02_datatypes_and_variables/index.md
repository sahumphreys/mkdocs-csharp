---
title: Introduction
---

# {{ title }}

!!! note "In this chapter, you will learn to:"

- Identify the difference between **variables** and **constants**.
- Use **assignment** to store values in variables and constants.
- Describe the use of **data types** and **casting**.
- Learn the difference between a **value type** and a **reference type**.
- Use **comments** effectively and understand their importance.

C# is an **explicitly, statically-typed language**. This means that every variable must be assigned a **data type** when it is declared, and that type cannot change later in the program. In C#, it’s not possible for a variable to exist without a defined type.

To understand why this matters, consider the following examples:

- `4`
- `"4"`
- `"four"`
- `4.0`

Each of these represents the value 4, but in a different way. They use different types of data to represent this value, so they need to be defined using different **data types** in our program, so the computer knows how to handle them correctly:

- The first, `4`, is a positive whole number with a numeric value, an **integer** (`int`).
- The second, `"4"`, is a single character, which has no numeric value, a **character** (`char`).
- The third, `"four"`, is a sequence of individual characters that spell out the word "four", but again, it has no numeric value, a **string** (`string`).
- The last, `4.0`, is a number that could include a fractional component; it has a numeric value, a **floating-point number** (`double`).

Although the values of the first and last examples are numerically the same, they will be interpreted differently by the computer because they are different data types.

This is true for all data types: each requires a different storage format and a different amount of **memory**. This affects how they are processed by the computer.

The value of the data is stored in a **variable**, which is a named portion of the computer's memory. In C#, when we declare a variable, we also specify its data type:

```cs
int myInt = 4;
char myChar = '4';
string myString = "four";
float myFloat = 4.0f;
```

Remember, each of these data items is just a pattern of binary digits (**bits**) when stored in the computer. The **data type** declared by the programmer determines how these bits are to be interpreted and what operations can be performed on them. For example, adding two integers with the `+` operator will yield a different result than adding two strings.

When writing programs, it is important to first think about the data you will be working with and processing. Consider the type of data you need: Are they whole numbers, characters, strings of characters, or fractional numbers? Choosing the right data type is crucial for accurate and efficient data processing.

This chapter will explore how variables are declared in C# and the importance of specifying their data type.
