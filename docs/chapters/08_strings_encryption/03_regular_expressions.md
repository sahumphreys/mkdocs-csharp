---
title: Regular Expressions in C\#
---

# {{ title }}

!!! note "From the syllabus"
    AQA: Know that a regular expression is simply a way of describing a set and that regular expressions allow particular types of languages to be described in a convenient shorthand notation; Be able to form and use simple regular expressions for string manipulation and matching. (4.4.2.3)

## Introduction to Regular Expressions

A regular expression (often abbreviated as regex or regexp) is a sequence of characters that defines a search pattern. They are incredibly useful for tasks such as:

- Validating input formats (e.g., email addresses, phone numbers).
- Extracting information from strings (e.g., dates, tags in HTML).
- Replacing or transforming substrings within a larger string.

### Basic Syntax

The syntax of a regular expression may look confusing at first, but once you understand the basics, they become a powerful tool. Let's break down a simple example to illustrate.

### Example: Matching a Date Format

Suppose you want to find dates in the format `"May 12"` or `"February 14"`. The corresponding regular expression pattern is:

```cs
string pattern = @"([a-zA-Z]+) (\d+)";
```

This pattern consists of:

- `@`: The `@` symbol denotes a __verbatim string__ in C#. This means backslashes are treated as literal characters, which is convenient for writing regex patterns.
- `([a-zA-Z]+)`: A group (`( )`) that matches one or more (`+`) uppercase or lowercase letters (`[a-zA-Z]`).
- `(\d+)`: A group that matches one or more digits (`\d`).

This pattern matches "May 12" or "February 14" but not "12 May" or "14 February".

## Common Regular Expression Patterns

Here are some common regex patterns and their meanings:

| Pattern  | Meaning                                      |
|----------|----------------------------------------------|
| `abc...` | Letters                                      |
| `123...` | Digits                                       |
| `\d`     | Any digit (equivalent to `[0-9]`)            |
| `\D`     | Any non-digit character                      |
| `.`      | Any character except newline                 |
| `\.`     | A literal full stop                          |
| `[abc]`  | Any one of 'a', 'b', or 'c'                  |
| `[^abc]` | Not 'a', 'b', or 'c'                         |
| `[a-z]`  | Any lowercase letter                         |
| `[0-9]`  | Any digit                                    |
| `\w`     | Any alphanumeric character (`[a-zA-Z0-9_]`)  |
| `\W`     | Any non-alphanumeric character               |
| `{m}`    | Exactly m repetitions                        |
| `{m,n}`  | Between m and n repetitions                  |
| `*`      | Zero or more repetitions                     |
| `+`      | One or more repetitions                      |
| `?`      | Zero or one repetition                       |
| `\s`     | Any whitespace                               |
| `\S`     | Any non-whitespace character                 |
| `^`      | Start of a string                            |
| `$`      | End of a string                              |
| `(abc\|def)` | Either 'abc' or 'def'                   |
| `(...)`  | Grouping                                     |

## Practical Examples

### Validating Email Addresses

A regular expression pattern to validate email addresses might look like this:

```cs
string emailPattern = @"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$";
```

Explanation:

- `^[a-zA-Z0-9._%+-]+`: Start with one or more letters, digits, dots, underscores, percent signs, plus or minus signs.
- `@[a-zA-Z0-9.-]+`: An `@` symbol followed by one or more letters, digits, dots, or hyphens.
- `\.[a-zA-Z]{2,}$`: A dot followed by 2 or more letters, representing the domain (e.g., .com, .org).

### Extracting HTML Tags

Let's extract all the HTML tags from a snippet of text:

```cs
using System;
using System.Text.RegularExpressions;

class Program
{
    static void Main()
    {
        string html = @"<p>The date of the next show will be <strong>May 12</strong></p>";
        string pattern = @"</?[a-z]+>";

        Regex rx = new Regex(pattern);
        MatchCollection matches = rx.Matches(html);

        foreach (Match match in matches)
        {
            Console.WriteLine(match.Value);
        }
    }
}
```

This pattern `</?[a-z]+>` matches:

- `<p>`, `<strong>`, `</strong>`, `</p>`.

Explanation:

- `</?`: Matches either `<` or `</` (the `?` makes the preceding `/` optional).
- `[a-z]+`: Matches one or more lowercase letters representing the tag name.

## Using Regular Expressions in C#

To use regular expressions in C#, import the `System.Text.RegularExpressions` namespace and use the `Regex` class.

### Basic Operations

- **Creating a Regex object:**
  ```cs
  Regex regex = new Regex(pattern);
  ```

- **Matching Patterns:**
  ```cs
  Match match = regex.Match(inputString);
  ```

- **Finding Multiple Matches:**
  ```cs
  MatchCollection matches = regex.Matches(inputString);
  ```

- **Replacing Text:**
  ```cs
  string result = regex.Replace(inputString, replacementString);
  ```

- **Splitting Strings:**
  ```cs
  string[] result = regex.Split(inputString);
  ```

### Matching and Extracting

Use the `Match` method to find the first match:

```cs
Match match = regex.Match(inputString);
if (match.Success)
{
    Console.WriteLine($"Found: {match.Value}");
}
```

### Replacing Text

Replace all digits in a string with an asterisk (`*`):

```cs
string input = "Phone: 123-456-7890";
string pattern = @"\d";
string result = Regex.Replace(input, pattern, "*");
Console.WriteLine(result);  // "Phone: ***-***-****"
```

### Splitting a String

Split a string based on whitespace characters:

```cs
string input = "Split this   sentence by   spaces.";
string pattern = @"\s+";
string[] words = Regex.Split(input, pattern);

foreach (string word in words)
{
    Console.WriteLine(word);
}
```

## Performance Considerations

- Be mindful of complex patterns that can degrade performance, especially in large texts or within loops.
- Use compiled regular expressions (`RegexOptions.Compiled`) for better performance in repeated use.

## Resources for Further Learning

Regular expressions can become quite complex. Explore the following resources for more in-depth learning:

- [RegexOne Tutorial](https://regexone.com/): Interactive tutorials for learning the basics.
- [Comprehensive C# Reference on RegexOne](https://regexone.com/references/csharp): In-depth guide on using regex in C#.

## Summary

- Regular expressions are powerful tools for text processing, validation, and transformation.
- Use verbatim strings (`@`) in C# to simplify regex patterns.
- Understand the most common patterns and their use cases.
- Practice with tools like RegexOne to master the basics.

Regular expressions can be challenging, but with practice, you'll be able to use them effectively in your C# programs.
