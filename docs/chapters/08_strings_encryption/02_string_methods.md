---
title: String Methods in C#
---

# {{ title }}

The `string` class in C# provides a variety of methods and properties for handling and processing strings. Below are some commonly used methods along with examples and explanations.

## Comparing Strings

### Using `Equals()`

The `Equals()` method checks if two strings are equal. It works similarly to the `==` operator but is generally preferred when dealing with objects.

```csharp
string word1 = "C#";
string word2 = "c#";

Console.WriteLine(word1.Equals("C#"));  // True
Console.WriteLine(word1.Equals(word2)); // False
Console.WriteLine(word1 == "C#");       // True
Console.WriteLine(word1 == word2);      // False
```

!!! note
    String comparison using `Equals()` is case-sensitive. To perform a case-insensitive comparison, use `Equals(word2, StringComparison.OrdinalIgnoreCase)`.

### Using `CompareTo()`

The `CompareTo()` method compares two strings based on their __lexicographical order__ (dictionary order).

- It returns `-1` if the first string is less than the second.
- It returns `0` if they are equal.
- It returns `1` if the first string is greater than the second.

```cs
string word1 = "Aardvark";
string word2 = "Adam";

Console.WriteLine(word1.CompareTo(word2)); // -1
```

!!! tip
    Remember that lowercase letters come after uppercase letters in ASCII order.

## Concatenation

Joining strings together can be done using the `+` operator or the `Concat()` method.

```cs
string hello = "Hello";
string world = "World";

Console.WriteLine(hello + " " + world);             // "Hello World"
Console.WriteLine(string.Concat(hello, " ", world)); // "Hello World"
```

### Concatenation with Other Data Types

```cs
string message = "Your age is ";
int age = 17;

message += age;  // "Your age is 17"
Console.WriteLine(message);
```

!!! note
    Avoid excessive use of `+` for string concatenation in loops, as it can affect performance. Consider using `StringBuilder` for repeated modifications.

## Changing Case

The methods `ToUpper()` and `ToLower()` convert all characters in a string to their uppercase or lowercase equivalents.

```cs
string password = "qwertyuiop";
Console.WriteLine(password.ToUpper());  // "QWERTYUIOP"
```

Use these methods for case-insensitive string comparisons or standardizing input.

## Searching for a Substring

### Using `IndexOf()`

The `IndexOf()` method searches for the first occurrence of a substring within a string and returns its index. It returns `-1` if the substring is not found.

```cs
string title = "Introduction to Computer Science";
Console.WriteLine(title.IndexOf("tro"));  // 2
Console.WriteLine(title.IndexOf("COMPUTER"));  // -1 (case-sensitive)
```

!!! tip
    Searches are case-sensitive. Convert both strings to the same case using `ToUpper()` or `ToLower()` for a case-insensitive search.

### Using `LastIndexOf()`

`LastIndexOf()` returns the index of the last occurrence of a substring within the string.

```cs
string text = "This is a test. This is only a test.";
Console.WriteLine(text.LastIndexOf("test"));  // 27
```

## Extracting a Substring

The `Substring()` method extracts a portion of the string starting from a specified index. Optionally, you can specify the length of the substring.

```cs
string title = "Introduction to Computer Science";
Console.WriteLine(title.Substring(16, 8));  // "Computer"
```

### Combining `IndexOf()` with `Substring()`

You can use `IndexOf()` to find the starting position of a substring and then use `Substring()` to extract it.

```csharp
string name = "Ms Robinson";
int charPos = name.IndexOf("R"); // Finds the position of 'R'
string lastName = name.Substring(charPos);
Console.WriteLine(lastName);     // "Robinson"
```

## Splitting a String

The `Split()` method breaks a string into an array of substrings based on a specified delimiter.

```csharp
string teams = "Arsenal,Chelsea,Everton,Liverpool";
string[] teamsArray = teams.Split(',');

foreach (string team in teamsArray)
{
    Console.WriteLine(team);
}
// OUTPUT:
// Arsenal
// Chelsea
// Everton
// Liverpool
```

!!! note
    If you need to split a string on multiple delimiters or with more complex logic, use `Regex.Split()`.

## Replacing a Substring

The `Replace()` method substitutes all occurrences of a specified substring with another substring.

```csharp
string message = "Hi John";
string newMessage = message.Replace("John", "Imran");
Console.WriteLine(newMessage);  // "Hi Imran"
```

`Replace()` is case-sensitive. Use it carefully when replacing text in a case-insensitive context.

## Escaping Characters in a String

Strings must be enclosed in double quotes (`"`). To include special characters, use escape sequences:

```csharp
string message = "Hello, my name is \"Khalid\" and I am from London";
Console.WriteLine(message);  // Hello, my name is "Khalid" and I am from London
```

### Common Escape Characters

| Escape Character | Result       | Description                            |
|------------------|--------------|----------------------------------------|
| `\\'`            | `'`          | Single quote                           |
| `\\"`            | `"`          | Double quote                           |
| `\\\\`           | `\`          | Backslash                              |
| `\\n`            | New Line     | Moves cursor to the beginning of the next line |
| `\\t`            | Tab          | Inserts a tab space                    |
| `\\b`            | Backspace    | Moves cursor back one space            |

Use escape sequences to handle characters like quotes and backslashes within your strings.

## Empty String

There are two equivalent ways to initialize an empty string in C#:

```csharp
string myString1 = String.Empty; // More readable and common
string myString2 = "";           // Equivalent to String.Empty

if (myString1 == String.Empty)
{
    Console.WriteLine("String is empty");
}
```

!!! note
    `string` is an alias for `System.String`. They can be used interchangeably.

## Summary

- C# provides a rich set of string methods for common operations like comparison, concatenation, and modification.
- Be aware of case sensitivity when using methods like `Equals()`, `IndexOf()`, and `Replace()`.
- Use escape sequences to handle special characters within strings.
- For complex string manipulation, consider using classes like `StringBuilder` for better performance.
