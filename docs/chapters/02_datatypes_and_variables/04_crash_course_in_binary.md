---
title: Crash Course in Binary
---

# {{ title }}

Everything that takes place in a computer depends on two-state switches. Each switch can be either **on** or **off**, which can be represented as either a $0$ or a $1$ (False or True).

We are familiar with the decimal (or denary) system, where each digit occupies a place equivalent to a power of $10$ (base $10$). In contrast, a two-state switch only needs a two-number system, known as **binary** (base $2$), where each digit occupies a place equivalent to a power of $2$.

Regardless of the base we are using, the digit with the greatest impact on the value is known as the **most significant digit**, while the digit with the least impact is referred to as the **least significant digit**.

Let’s start with denary and take the number $245_{10}$ as an example. This number consists of:

- $2$ hundreds
- $4$ tens
- $5$ ones (units)

Thus, $(2 \times 100) + (4 \times 10) + (5 \times 1) = 245$.

That is:

| $10^{3}$ | $10^{2}$ | $10^{1}$ | $10^{0}$ |
| --------- | --------- | --------- | --------- |
|     0     |     2     |     4     |     5     |

Our number system also accommodates numbers with fractional parts. Thus, $245.68_{10}$ would be represented as:

$(2 \times 100) + (4 \times 10) + (5 \times 1) + (6 \times \frac{1}{10}) + (8 \times \frac{1}{100}) = 245.68$

That is:

| $10^{3}$ | $10^{2}$ | $10^{1}$ | $10^{0}$ | . | $10^{-1}$ | $10^{-2}$ | $10^{-3}$ |
| --------- | --------- | --------- | --------- | - | --------- | --------- | --------- |
|     0     |     2     |     4     |     5     | . |     6     |     8     |     0     |

Now, let's compare the principle of positional value with the binary representation of the decimal number $13_{10}$.

The column headings for our binary system and their respective values are:

| $2^{7}$ | $2^{6}$ | $2^{5}$ | $2^{4}$ | $2^{3}$ | $2^{2}$ | $2^{1}$ | $2^{0}$ |
| ------- | ------- | ------- | ------- | ------- | ------- | ------- | ------- |
|   128   |    64   |   32    |   16    |    8    |     4   |    2    |    1    |

Thus, $13$ will be one lot of $8$, one lot of $4$, and one lot of $1$:

Hence, $(1 \times 8) + (1 \times 4) + (1 \times 1) = 13$.

That is:

| $2^{3}$ | $2^{2}$ | $2^{1}$ | $2^{0}$ |
| ------- | ------- | ------- | ------- |
|    1    |    1    |    0    |    1    |

## Range of Values

This has significant implications for our data types, memory allocation, and the range of values that can be stored in memory. Clearly, if we have only a single bit, then only two different values can be stored: $0$ and $1$. This is all we need for a `bool` data type.

How many different values can we store in $8$ bits? The answer is $2^{8}$, or $256$. Accounting for zero, this means a byte of memory can have a range of values between $0$ and $255$. Referring to the table of C# data types, we can see this is the case with the `byte` data type. The `sbyte` includes both negative and positive numbers, thus allowing the same range of values but with different magnitudes.

Consequently, our `int` data type, which has $4$ bytes (or $32$ bits) allocated to it, will have a range of $2^{32}$ different values, both negative and positive.

## Signed and Unsigned Numbers

Using the binary number system to represent voltages (on or off) presents a challenge when needing a third symbol to represent a minus sign ('-'). We must use the two symbols we have, '0' and '1', to represent both the size and the sign of any number. There are various methods to do this, but here we will consider the **two's complement** method. Two's complement representation uses the most significant bit as the sign bit, which is always negative. Consider the following table:

| $2^{-2}$ | $2^{1}$ | $2^{0}$ | Decimal |
| ------- | ------- | ------- | ------- |
| 0       | 0       | 0       | 0       |
| 0       | 0       | 1       | 1       |
| 0       | 1       | 0       | 2       |
| 0       | 1       | 1       | 3       |
| 1       | 0       | 0       | -4      |
| 1       | 0       | 1       | -3      |
| 1       | 1       | 0       | -2      |
| 1       | 1       | 1       | -1      |

Each of the negative numbers now has a $1$ as its most significant bit, while the positive numbers have $0$ in that position. Take note of some other observations:

- The most negative value has $1$ in the most significant bit, and all other values are set to $0$.
- For $-1$, every bit is set to $1$.
- The most positive value has $1$ in every position except for the most significant bit, which is $0$.
- Using $3$ bits, the number of values possible is $2^3 = 8$, but the range is $-4$ to $+3$.

## Converting Decimal to Two's Complement Binary

There are two methods for converting decimal to two's complement. Before using either method, convert the decimal integer to binary. Ignore whether the decimal number is negative; treat it as positive and follow either method 1 or 2 below:

- **Method 1:** Invert all of the binary values, and then add $1$.
- **Method 2:** Start with the least significant bit, copy down all values up to and including the first $1$ encountered, and then flip the remaining digits.

For example, using Method 1, let’s convert $-23$:

1. Convert $23$ to binary: $00010111_2$
2. Invert all the digits: $11101000_2$
3. Add $1$: $11101001_2$

This can be illustrated with some C# code:

```csharp
static void Main(string[] args)
{
    int value = 23;
    Console.WriteLine($"{value} in binary is: {Convert.ToString(value,2)}");
    value = ~value;
    Console.WriteLine($"Flip the bits  : {Convert.ToString(value,2)} ({value})");
    value++;
    Console.WriteLine($"Add 1          : {Convert.ToString(value,2)} ({value})");
}
```

This code gives the following output:

```bash
23 in binary is: 10111
Flip the bits  : 11111111111111111111111111101000 (-24)
Add 1          : 11111111111111111111111111101001 (-23)
```

The bitwise operator `~` (see chapter 3) performs a NOT operation on each bit, changing a `1` to a `0` and vice versa.

## Fractional Numbers

Similar to denary, binary numbers with fractional parts work in the same way, where the column headings after the binary point will be $\frac{1}{2}$, $\frac{1}{4}$, $\frac{1}{8}$, etc.

| $2^{3}$ | $2^{2}$ | $2^{1}$ | $2^{0}$ | . | $2^{-1}$ | $2^{-2}$ | $2^{-3}$ | $2^{-4}$ |
| ------- | ------- | ------- | ------- | - | ------- | ------- | ------- | ------- |
|    8    |    4    |    2    |    1    |   |  0.5   |  0.25  |  0.125 | 0.0625 |

Consider the binary value $1001.1100_{2}$:

| $2^{3}$ | $2^{2}$ | $2^{1}$ | $2^{0}$ | . | $2^{-1}$ | $2^{-2}$ | $2^{-3}$ | $2^{-4}$ |
| ------- | ------- | ------- | ------- | - | ------- | ------- | ------- | ------- |
|    1    |    0    |    0

    |    1    | . |    1    |    1    |    0    |    0    |

This can be calculated as follows:

$1 \times 8 + 0 \times 4 + 0 \times 2 + 1 \times 1 + 1 \times 0.5 + 1 \times 0.25 + 0 \times 0.125 + 0 \times 0.0625 = 9.75_{10}$.

## Fixed and Floating Point Representation

With fixed-point representation, the binary point is placed at a fixed position, typically to the right of the whole number. This restricts the range of values that can be stored, as moving the binary point affects the scale.

In contrast, floating-point representation uses a formula for dynamic placement of the binary point, allowing for a much wider range of values. A floating-point number is typically expressed in the form of `sign × significand × base^exponent`.

While this allows for greater flexibility, floating-point arithmetic can introduce rounding errors. This is an important consideration when performing calculations in programming.

## Hexadecimal System

The hexadecimal (or hex) system provides a convenient shorthand for binary representation. Since $16$ is $2^4$, each hex digit corresponds to $4$ binary digits. Thus, the binary representation can be easily converted to hex and vice versa.

For example, the binary number $11010101_2$ can be grouped into sets of four digits from the right:

| Binary  | Hex |
| ------- | --- |
| 1101    | D   |
| 0101    | 5   |

Thus, $11010101_2$ is equal to $D5_{16}$.

## Exercises

1. Write a C# program to convert a decimal number to binary.
2. Convert the binary number $1011.0110_2$ to decimal.
3. Write a program to demonstrate signed and unsigned overflow for an integer.
