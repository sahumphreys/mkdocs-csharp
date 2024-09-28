---
title: Type Conversion
---

# {{ title }}

In programming, it is often necessary to change the value of a variable from one data type to another. For example, converting an `int` to a `double`. There are two primary approaches for this: **casting** and **conversion**.

## Casting

**Casting** is a method of explicitly changing one data type to another, where permissible. To perform an explicit cast, precede the variable with the new type in parentheses, as illustrated below:

```cs
float height = 4.23f;
double maxHeight = height;              // Implicit cast; no need to specify
double minHeight = (double)height;      // Explicit cast
float realHeight = (float)minHeight;    // Explicit cast
```

In this example:
- The variable `maxHeight` is assigned the value of `height` without explicit casting since a `float` can be implicitly converted to a `double`.
- The variable `minHeight` is explicitly cast to a `double`.
- The variable `realHeight` demonstrates an explicit cast back to `float`.

It is safe to cast from an `int` to a `double` since there is **no risk of data loss**. However, casting from a `decimal` to an `int` may lead to loss of precision, as the `decimal` type is more precise than `int`. This type of cast should be approached cautiously.

## Conversion with the Convert Class

Alternatively, we can use the `Convert` class, which provides methods to convert any primitive type into another primitive type. Notably, converting from a `float` to an `int` will truncate any decimal values:

```cs
int i = 42;
double f = Convert.ToDouble(i);         // Converts int to double
decimal m = 4.99m;
int im = Convert.ToInt32(m);            // Converts decimal to int, truncating the value
Console.WriteLine("{0} {1} {2} {3}", i, f, m, im); // Outputs: 42 42 4.99 4
Console.WriteLine(im.ToString());       // Outputs: "4"
```

In this example:
- The value of `m` is converted to an `int`, resulting in a truncation of the decimal part, yielding `4` instead of `5`.

In general, using the `Convert` class is safer than casting and is more likely to succeed without causing exceptions.

## Converting from Strings

When converting from a `string` to another data type, more careful handling is required. If the conversion fails, an **exception** will be thrown. To handle this more gracefully, you can use either the `Parse()` method or, preferably, the `TryParse()` method.

```cs
int i = int.Parse(Console.ReadLine());  // Throws an exception if input is not numeric

int result;
bool isValid = int.TryParse(Console.ReadLine(), out result);
if (isValid)
    Console.WriteLine(result);            // Outputs the converted integer
else
    Console.WriteLine("Input is not in the correct format.");
```

In this code:
- The `Parse()` method will throw an exception if the user input is not a valid numeric value.
- The `TryParse()` method returns a `bool`, indicating whether the conversion was successful. If successful, the converted value is stored in the `out` parameter, `result`.

## Summary

- **Casting** is an explicit way to convert types when there is no risk of data loss.
- **Conversion** using the `Convert` class is generally safer and more flexible.
- Always handle string conversions carefully, using `TryParse()` to avoid exceptions from invalid inputs.

By understanding and utilizing these type conversion methods effectively, you can write more robust and error-free code in C#.
