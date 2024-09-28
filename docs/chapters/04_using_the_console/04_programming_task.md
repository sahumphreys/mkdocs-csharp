---
title: Programming Task -  Formatting data to the console
---

# {{ title }}

Write a program that asks the user for __three__ numbers then prints these numbers in three virtual columns on the console.

- Each column should have a width of 10 characters and the numbers should be left aligned.
- The first number should be an integer in hexadecimal;
- the second should be fractional positive;
- and the third a negative fraction.
- The last two numbers have to be rounded to the second decimal place.

The following table summaries the format specifiers:

| Code  |  Name      |           Example                              |
| ------| ---------- | ---------------------------------------------- |
| C, c  | Currency   |`Console.WriteLine("{0:C2}", 14.99); // £14.99`|
| D, d  | Digits     |`Console.WriteLine("{0:D8}", 19);    // 00000019`|
| E, e  | Exponential|`Console.WriteLine("{0:E3}", 245);   // 2.450E+002`|
| F, f  | Float      |`Console.WriteLine("{0:F4}", 42);     // 42.0000`|
| N, n  | Number     |`Console.WriteLine("{0:N0}", 42.3);    // 42` |
| P, p  | Percentage |`Console.WriteLine("{0:P1}",0.112);  // 11.2%`|
| X, x  | Hexadecimal|`Console.WriteLine("{0:X}", 255);    // FF`|
