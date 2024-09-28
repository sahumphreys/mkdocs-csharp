---
title: ASCII and Unicode
---

!!! note "From the syllabus"
    AQA: Describe ASCII and Unicode coding systems for coding character data and explain why Unicode was introduced. (3.5.5.2/4.5.5.2)

In ASCII, every letter, punctuation mark, digit, etc., is assigned a 7-bit code. .NET uses a 16-bit standard, but Unicode also includes 8-bit and 32-bit code units. Unicode can support a much wider range of characters from various languages, including Arabic, Greek, mathematical symbols, historical scripts, and even emojis.

One of the exercises from the end of the last chapter was:

- **Write a program that takes as input a four-digit number and calculates the sum of its digits.**

For instance, if the number entered is 1234, we calculate \(1 + 2 + 3 + 4\).

From mathematics, we know that dividing by 10 and taking the remainder works for extracting digits. For example:

```cs
int num = Convert.ToInt32(Console.ReadLine());
int a = num % 10;
int b = (num / 10) % 10;
int c = (num / 100) % 10;
int d = (num / 1000) % 10;
```

While this is a valid solution, let's briefly explore character data entered at the keyboard and see what happens "under the hood."

In this example, we want to read a single character from the keyboard. We know `Console.ReadLine()` reads a string (a sequence of characters), and we can obtain the first character from that input string using its index `[0]`. Thus, to get the first character from the string, we use `Console.ReadLine()[0]`.

Here's a code sample using this command. Can you predict what will be displayed on the screen if the user enters '3'?

```cs
char ch;
Console.Write("Enter a character > ");
ch = Console.ReadLine()[0];
int n = 4 + ch;                 // Implicitly casting to an integer
Console.WriteLine(n);
```

What about in this example?

```cs
char ch;
Console.Write("Enter a character > ");
ch = Console.ReadLine()[0];
int n = 4 + (int)ch;            // Explicitly casting character to an integer
Console.WriteLine(n);
```

In both cases, the output will be 55. If you were expecting it to be 7, you might be surprised.

"Under the hood," all character data is represented to the processor as a numeric code. The processor can only process binary data, so letters need to be converted into binary. This conversion applies to numeric characters '0' - '9' as well. Originally, the **ASCII** (American Standard Code for Information Interchange) was developed. This used a byte to encode the alphabet, digits, punctuation, and some control codes and non-printing characters (such as 'TAB' and 'LINE FEED'). This approach worked well for English but was less effective for other languages like Greek or Arabic. Consequently, a different code was developed: **Unicode**, which uses 16 bits (with 8-bit and 32-bit options available as well).

## ASCII Codes for Digits

Here is the ASCII code for the digits:

| Decimal | Hex | Char |
|---------|-----|------|
| 48      | 30  | 0    |
| 49      | 31  | 1    |
| 50      | 32  | 2    |
| 51      | 33  | 3    |
| 52      | 34  | 4    |
| 53      | 35  | 5    |
| 54      | 36  | 6    |
| 55      | 37  | 7    |
| 56      | 38  | 8    |
| 57      | 39  | 9    |

This table explains why 55 is the output from our program: it displays the ASCII code for the character '7'!

To convert the character '2' to its integer value, we need to subtract 48 from the input (or subtract '0', which also works).

```cs
char ch;
Console.Write("Enter a character > ");
ch = Console.ReadLine()[0];         // Read just the first character of input
int n = 4 + (ch - 48);              // Subtracting ASCII code for '0' to get value
Console.WriteLine(n);
```

C# allows us to **cast** a character to its integer ASCII value and vice versa:

```cs
char letter = (char)97;         // 'a'     
```

```cs
char letter = 'a';
int asciiValue = (int)letter;
```

To work with an entire string, we can use the `GetBytes()` method from the `Encoding.ASCII` namespace, which converts a string into an array of bytes:

```cs
string fullName = "Harry Lime";
byte[] bytes = Encoding.ASCII.GetBytes(fullName);
foreach (byte b in bytes)
{
    Console.WriteLine(b);
}
```

Unicode characters can be displayed using their hexadecimal code preceded by `\u`. For instance, the Unicode for 'A' is `\u0041`, and for 'a' it is `\u0061`. All four digits must be present after the `\u` indicator since .NET uses 16-bit Unicode, with each code symbol representing one byte.

!!! note
    Not all Unicode characters will print to your console; you need to have a font installed that can display certain characters. If a character cannot be displayed, a question mark will be used instead.

To learn more about Unicode, check out [the absolute minimum every software developer absolutely positively must know about Unicode and character sets](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/).
