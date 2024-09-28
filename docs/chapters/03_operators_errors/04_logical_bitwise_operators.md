---
title: Logical and Bitwise Operators
---

# {{ title }}

## Logical Operators

!!! note "From the syllabus"
    AQA: Be familiar with and be able to use ... (3.1.1.4/4.1.1.4)
    
    - NOT, AND, OR, XOR

Logical operators work on Boolean values (true or false), returning a Boolean result. In the table below, assume `a = true` and `b = false`:

| Operator | Description | Example         |
| -------- | ----------- | ---------------- |
| `&&`     | AND         | `a && b` -> False |
| `\|\|`   | OR          | `a \|\| b` -> True |
| `!`      | NOT         | `!a` -> False    |

**Example**

```cs
bool a = true;
bool b = false;
Console.WriteLine(a && b);              // false
Console.WriteLine(a || b);              // true
Console.WriteLine(!a);                  // false
Console.WriteLine(b || true);           // true
```

## Bitwise Operators

Bitwise operators are similar to logical operators but operate at the bit level (0 and 1). These operators can be challenging to understand but are essential in various applications, especially in low-level programming and performance optimization.

In the table below, assume `a = 5` (binary `0101`) and `b = 9` (binary `1001`):

| Operator | Description         | Example         |
| -------- | ------------------- | ---------------- |
| `&`      | Bitwise AND         | `a & b` -> `1`  |
| `\|`     | Bitwise OR          | `a \| b` -> `13` |
| `^`      | Bitwise XOR         | `a ^ b` -> `12`  |
| `~`      | Bitwise NOT         | `~a` -> `-6`    |

Also, two shift operators:

| Operator | Description                                    | Example         |
| -------- | ---------------------------------------------- | ---------------- |
| `<< n`   | Shift bits to the left by `n` places          | `a << 1` -> `10` (equivalent to `a * 2`) |
| `>> n`   | Shift bits to the right by `n` places         | `b >> 2` -> `2` (equivalent to `b / 4`) |

**Truth Tables**

Understanding the outcomes of bitwise operations can be simplified by using truth tables. Below is a truth table for the logical operations AND, OR, and XOR:

| `a` | `b` | `a & b` | `a \| b` | `a ^ b` |
| --- | --- | ------- | -------- | ------- |
| 0   | 0   |   0     |    0     |   0     |
| 0   | 1   |   0     |    1     |   1     |
| 1   | 0   |   0     |    1     |   1     |
| 1   | 1   |   1     |    1     |   0     |

**Example**

```cs
byte a = 5; // 0101 in binary
byte b = 9; // 1001 in binary
Console.WriteLine(a & b);       // 1 (binary 0001)
Console.WriteLine(a | b);       // 13 (binary 1101)
Console.WriteLine(a ^ b);       // 12 (binary 1100)
Console.WriteLine(~a);          // -6 (in two's complement)
Console.WriteLine(a << 1);      // 10 (binary 1010)
Console.WriteLine(b >> 2);      // 2 (binary 0010)
```

If you are unsure why these are the results, do the calculations on paper, referencing the binary representations of `a` and `b`.

### Common Uses

Bitwise operations are often used for "bit twiddling," such as masking certain bits. For example, you can check if a value is odd or even by masking the least significant bit:

```cs
int number = 6;
if ((number & 1) == 0)
{
    Console.WriteLine($"{number} is even.");
}
else
{
    Console.WriteLine($"{number} is odd.");
}
```

The XOR operator is also handy for swapping values without needing a temporary variable:

```cs
static void Main(string[] args)
{
    int a = 5;
    int b = 9;
    Console.WriteLine($"Before swap: a = {a}, b = {b}");
    a ^= b;
    b ^= a;
    a ^= b;
    Console.WriteLine($"After swap: a = {a}, b = {b}");
}
```

### Checking for Powers of 2
To check if a number is a power of `2`, you can use the following method:

```cs
int n = 256;
if ((n & (n - 1)) == 0 && n != 0)
    Console.WriteLine($"{n} is a power of 2");
else
    Console.WriteLine($"{n} is not a power of 2");
```

This works because a power of `2` has exactly one bit set in its binary representation. For example, `256` in binary is `100000000`, and `255` (which is `256 - 1`) is `011111111`, thus `n & (n - 1)` results in `0`.

### Multiplication and Division via Shifts
Shifting bits left or right is equivalent to multiplying or dividing by `2`, respectively. For example:

- `a << 1` doubles `a` (shifts left by one bit).
- `b >> 2` divides `b` by `4` (shifts right by two bits).
