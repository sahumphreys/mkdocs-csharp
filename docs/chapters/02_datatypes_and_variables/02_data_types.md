---
title: Data Types
---

# {{ title }}


!!! note "From the syllabus"
    Understand the concept of a data type (3.1.1.1/4.1.1.1); Understand and use integer, real/float, Boolean, character, string, date/time, pointer/reference, records/structs, arrays/lists (3.1.1.1/4.1.1.1).
    
    A data type describes the kind of data being stored or processed by a program, such as character or numeric values. Different programming languages define different data types, and many allow users to create their own custom types from these built-in ones.

A **data type** is a set of values that share similar characteristics, such as:

- **Name**: e.g., `int` or `bool`.
- **Size**: the amount of memory they occupy, measured in bytes or bits.
- **Default Value**: the initial value they take, e.g., `0` for integers.

## Primitive Data Types in C#

The following are the basic, or **primitive**, data types used in C#:

- **Integer types**: `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`
- **Real floating-point types**: `float`, `double`
- **Real type with decimal precision**: `decimal`
- **Boolean type**: `bool`
- **Character type**: `char`
- **String**: `string`
- **Object type**: `object`

These are called **primitive data types**[^prim] because they are built into the C# language. The following table summarizes their characteristics:

| Type   | Default Value | Minimum                     | Maximum                    | Size (bytes) |
|--------|---------------|----------------------------|----------------------------|--------------|
| sbyte  | 0             | -128                       | 127                        | 1            |
| byte   | 0             | 0                          | 255                        | 1            |
| short  | 0             | -32768                     | 32767                      | 2            |
| ushort | 0             | 0                          | 65535                      | 2            |
| int    | 0             | -2147483648                | 2147483647                 | 4            |
| uint   | 0u            | 0                          | 4294967295                 | 4            |
| long   | 0L            | -9223372036854775808       | 9223372036854775807        | 8            |
| ulong  | 0UL           | 0                          | 18446744073709551615       | 8            |
| float  | 0.0f          | ±1.5 × 10<sup>-45</sup>    | ±3.4 × 10<sup>38</sup>     | 4            |
| double | 0.0d          | ±5.0 × 10<sup>-324</sup>   | ±1.7 × 10<sup>308</sup>    | 8            |
| decimal| 0.0m          | ±1.0 × 10<sup>-28</sup>    | ±7.9 × 10<sup>28</sup>     | 16           |
| bool   | false         | true                       | false                      | 1 bit        |
| char   | '\u0000'      | '\u0000'                   | '\uffff'                   | 2            |
| string | null          | -                          | -                          | -            |
| object | null          | -                          | -                          | -            |

### Integer Types

Integer types are used for whole numbers. Each type varies by the range of values it can hold, depending on the amount of memory allocated and whether the numbers are **signed** (both positive and negative) or **unsigned** (positive only). Of these, the most commonly used is `int`, which uses 32 bits.

!!! note
    Integer values can be represented in different notations: 
    - **Decimal** (base 10): `int num = 20;`
    - **Hexadecimal** (base 16): `int num = 0x14;`
    - **Binary** (base 2): `int num = 0b10100;`

### Real Floating-Point Types

Real floating-point types are used for numbers with a fractional component. C# provides three such types:

- **float** (single precision)
- **double** (double precision, default for floating-point numbers)
- **decimal** (decimal precision, often used for financial calculations)

Because all floating-point numbers default to `double` in C#, you need to use the 'f' suffix for `float` and 'm' for `decimal`:

```cs
float myFloat = 3.14f;
decimal myDecimal = 3.14m;
```

Floating-point numbers are an approximation of mathematical real numbers, meaning that there are an infinite number of values between any two real numbers. However, computers use a fixed number of bits to represent them, which can lead to precision issues.

**Example: Precision Differences**

```cs
// Declare some variables
float floatPI = 3.141592653589793238f;
double doublePI = 3.141592653589793238;

// Print the results on the console
Console.WriteLine("Float PI is: " + floatPI);
Console.WriteLine("Double PI is: " + doublePI);

// Console output:
// Float PI is: 3.141593
// Double PI is: 3.14159265358979
```

Here, the `float` value is rounded to 7 digits, whereas the `double` retains up to 15 digits. If you require this level of precision, use `double`.

#### Floating-Point Precision Errors

Floating-point arithmetic can produce unexpected results due to precision limitations. Consider the following example:

```cs
float f = 0.1f;
Console.WriteLine(f); // 0.1

double d = 0.1f;
Console.WriteLine(d); // 0.100000001490116

float ff = 1.0f / 3;
Console.WriteLine(ff); // 0.3333333

double dd = ff;
Console.WriteLine(dd); // 0.333333343267441
```

These rounding errors can be avoided by using the `decimal` type, which uses more memory (16 bytes) and performs calculations with the decimal system rather than binary. This makes `decimal` ideal for financial applications where precision is critical. However, because they require more memory and processing power, operations with `decimal` are slower than with `double`.

### Boolean Type

The `bool` type has only two values: `true` and `false`. It is primarily used for logical expressions and decision-making.

### Character Type

The `char` type represents a single character, using 16-bit Unicode encoding. Characters are enclosed in single quotes, e.g., `'a'`, `'r'`. Each `char` has a corresponding binary code, either ASCII or Unicode.

## String Type

A `string` is a sequence of characters enclosed in double quotes, e.g., `"Hello"`. `strings` in C# are actually objects and are more complex than primitive types.

## Object Type

The `object` type is the base type for all .NET types. Any type in C# can be assigned to an `object` variable. This makes it very flexible but also more memory-intensive.

We'll explore how these various types can be organized into **data structures** such as arrays, lists, structs, and classes in future lessons.

[^prim]: Strictly speaking, the `string` and `object` types are not primitive but reference data types. Primitive data types are also called **value types** because their values are stored directly on the program stack. Reference types, on the other hand, store a memory address pointing to the actual data, which is located in dynamic memory (the heap).
